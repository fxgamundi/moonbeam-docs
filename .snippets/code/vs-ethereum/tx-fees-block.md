```ts
import axios from 'axios';

// This script calculates the transaction fees of all transactions in a Moonbeam block according to the transaction type (For Ethereum API: legacy, EIP-1559 or EIP-2930 standards, and Substrate API), as well as calculating the total fees in the block. 

// Endpoint to retrieve the latest block
const endpointBlock = 'http://127.0.0.1:8080/blocks/head';
// Endpoint to retrieve the node client's information
const endpointNodeVersion = 'http://127.0.0.1:8080/node/version';

async function main() {

    try {
        // Create a variable to sum the transaction fees in the whole block
        var totalFees = 0;

        // Find which Moonbeam network the Sidecar is pointing to
        const response_client = await axios.get(endpointNodeVersion);
        const network = response_client.data.clientImplName;

        // Retrieve the block from the Sidecar endpoint
        const response_block = await axios.get(endpointBlock);
        // Retrieve the block height of the current block
        console.log('Block Height: '+response_block.data.number)

        // Iterate through all extrinsics in the block
        response_block.data.extrinsics.forEach(extrinsic => {
            // Create an object to store transaction information
            var transactionData = new Object()
            // Set the network field
            transactionData["network"] = network;

            // Filter for Ethereum Transfers
            if (extrinsic.method.pallet === 'ethereum' && extrinsic.method.method === 'transact'){

                // Iterate through the events to get non type specific parameters
                extrinsic.events.forEach(event => {
                    if (event.method.pallet === 'ethereum' && event.method.method === 'Executed') {
                        transactionData["hash"] = event.data[2];
                    }
                    if (event.method.pallet === 'system' && event.method.method === 'ExtrinsicSuccess') {
                        transactionData["weight"] = event.data[0].weight;
                    }
                });

                // Get the transaction type and type specific parameters and compute the transaction fee
                if (extrinsic.args.transaction.legacy) {
                    transactionData["txType"] = "legacy";
                    transactionData["gasPrice"] = extrinsic.args.transaction.legacy.gasPrice
                    transactionData["txFee"] = transactionData["gasPrice"] * transactionData["weight"] / 25000
                } 
                else if (extrinsic.args.transaction.eip1559) {
                    transactionData["txType"] = "eip1599";
                    transactionData["maxPriorityFeePerGas"] = extrinsic.args.transaction.eip1559.maxPriorityFeePerGas
                    // Set the network base fee
                    if (transactionData["network"] == "moonbeam"){
                        transactionData["baseFee"] = 100000000000;
                    } else {
                        transactionData["baseFee"] = 1000000000;
                    }
                    transactionData["txFee"] = (transactionData["baseFee"] + transactionData["maxPriorityFeePerGas"]) * transactionData["weight"] / 25000
                } 
                else if (extrinsic.args.transaction.eip2930) {
                    transactionData["txType"] = "eip2930";
                    transactionData["gasPrice"] = extrinsic.args.transaction.eip2930.gasPrice
                    transactionData["txFee"] = transactionData["gasPrice"] * transactionData["weight"] / 25000
                }

                // Increment totalFees
                totalFees += transactionData["txFee"]

                // Display the tx information to console
                console.log(transactionData)
            }
            // Filter for Substrate transactions, check if the extrinsic has a "TransactionFeePaid" event
            else {
                extrinsic.events.forEach(event => {
                    if (event.method.pallet === 'transactionPayment' && event.method.method === 'TransactionFeePaid') {
                        transactionData["txType"] = "substrate";
                        transactionData["txFee"] = event.data[1];
                        transactionData["tip"] = event.data[1];
                    }
                    if (event.method.pallet === 'system' && event.method.method === 'ExtrinsicSuccess') {
                        transactionData["weight"] = event.data[0].weight;
                    }
                });
            }

        });

        // Output the total amount of fees in the block
        console.log('Total fees in block: ' + totalFees)
    } catch (err) {
        console.log(err);
    }
}

main()
```
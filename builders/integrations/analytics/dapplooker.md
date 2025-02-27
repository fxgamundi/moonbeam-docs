---
title: Dapplooker
description: Use Dapplooker to analyze and query on-chain data, and create dashboards to visualize analytics for Moonbeam and Moonriver.
---

# Getting Started with Dapplooker

![Dapplooker Banner](/images/builders/integrations/analytics/dapplooker/dapplooker-banner.png)

## Introduction {: #introduction }

Developers on Moonriver and Moonbeam can use the [Dapplooker](https://dapplooker.com/){target=_blank} platform to analyze their on-chain data and run SQL queries. The integration gives projects the ability to create charts and dashboards to track their smart contracts and provide feedback on performance and adoption.

Dapplooker analytics platform complements Moonbeam-based networks by helping users make sense of smart contracts without having to rely on an engineer or analyst. Dapplooker’s intuitive Visual SQL helps browse smart contract data in tabular form and write SQL queries using easy to use editor. Users can create, fork and share dashboards with everyone.

This guide will cover all of the details needed to register your project with the Dapplooker platform and how to build analytics using SQL editor. This guide can be adapted for use on Moonbeam, Moonriver, or Moonbase Alpha.

--8<-- 'text/disclaimers/third-party-content-intro.md'

## Checking Prerequisites {: #checking-prerequisites }

To get started with this guide, you'll need to create or have a Dapplooker account. You can [signup](https://dapplooker.com/signup){target=_blank} and create an account. If you already have signed up, you can [login](https://dapplooker.com/login){target=_blank} to your account. 

![Login to Dapplooker](/images/builders/integrations/analytics/dapplooker/dapplooker-1.png)

## Connect Smart Contracts {: #connect-smart-contracts }

To connect a smart contract to Dapplooker, you can click on the **My Projects** button at the top of the page.

From the **Register Your Project** page, click **Connect Dapp** then select the **Connect Smart Contract** option. You can also browse and run analytics on already indexed DApps from the menu.

![Connect dapp](/images/builders/integrations/analytics/dapplooker/dapplooker-2.png)

You'll be prompted to enter in details about your project and contract:

1. Enter your project name
2. Enter the network your project lives on. The network can be either **Moonbeam**, **Moonriver**, or **Moonbase Alpha**
3. Toggle the slider if you have several instances of the same contract
4. Enter your contract address. If the contract address is verified on [Moonscan](https://moonscan.io/){target=_blank}, it will start appearing in autocomplete. You can select the contract address from autocomplete. If no contract address appears in autcomplete, you can input your contract address and click on the **+** button and then the upload button to upload the ABI
5. Enter your project's website
6. Upload your project's logo
7. Click **Register** and smart contract transactions events data syncing will start. It can take some time for complete data to be synced

![Register your dapp](/images/builders/integrations/analytics/dapplooker/dapplooker-3.png)

Once syncing is complete, you will get an email notification. Clicking on the link in the email will take you directly to your indexed data.

## Connect Subgraphs {: #connect-subgraphs }

To connect a subgraph to Dapplooker, you can click on the **My Projects** button at the top of the page.

From the **Register Your Project** page, click **Connect Dapp** then select the **Connect Subgraph** option. You can also browse and run analytics on already indexed Dapps from the menu.

![Connect dapp](/images/builders/integrations/analytics/dapplooker/dapplooker-4.png)

You'll be prompted to enter in details about your project and subgraph:

1. Enter your project name
2. Enter the network your project lives on. The network can be either **Moonbeam**, **Moonriver**, or **Moonbase Alpha**
3. Input your DApp subgraph endpoint
4. Enter your project's website
5. Upload your project's logo
6. Click **Register** and subgraph entities data syncing will start. It can take some time for complete data to be synced

![Register your dapp](/images/builders/integrations/analytics/dapplooker/dapplooker-5.png)

Once syncing is complete, you will get an email notification. Clicking on the link in the email will take you directly to your indexed data.

## Create Charts & Dashboards {: #create-charts-dashboards }

To get started creating charts to visualize your data, you can click **Create a Chart** at the top of the page. From there you can choose to create a **Simple chart**, **Custom chart**, or **Native query** chart. For more information on creating each type of chart, you can take a look at the [Dapplooker documentation on creating charts](https://dapplooker.notion.site/Create-Charts-9cd44e01cb0f472d835e8f2d954e517a){target=_blank}.

If you are interested in creating a dashboard, you can get started by clicking **Browse Data** at the top of the page. Then you can select the **+** button which will have a dropdown menu where you can select **New dashboard**. For more information on creating a dashboard, please refer to the [Dapplooker documentation on creating a dashboard](https://dapplooker.notion.site/Create-Dashboard-e2023db32c2342969194134a5fb9780b){target=_blank}.

You can publish charts and dashboards in private or public folders. Public charts and dashboards are accessible to everyone. You can also fork, edit, and create new charts and dashboards from public charts.

## Example Charts & Dashboards {: #example-dashboards }

There are a collection of charts and dashboards available for you to view and build off of for both Moonbeam and Moonriver. To get started, you can take a look at the [Moonbeam Network Collection](https://analytics.dapplooker.com/collection/323-moonbeam-network-collection){target=_blank} or the [Moonriver Network Collection](https://analytics.dapplooker.com/collection/79-moonriver-network-collection){target=_blank}. From there you'll find a list of public charts and dashboards that can easily be edited.

To start editing any of the charts or dashboards, you can click on the list icon in the right hand corner between the **Summarize** button and the refresh icon. This will take you to the editor where you can fully customize the preexisting data. Any changes you make will not automatically be saved. To create the chart or dashboard with your changes, you'll need to click **Save**. For more information on editing and creating the charts or dashboards, please refer to the [Dapplooker documentation site](https://dapplooker.notion.site/Features-1454c891aef34dedb4e3067195e02245){target=_blank}.

Another place you can start to view and build off of data is from the list of [Moonbeam Staking dashboards](https://analytics.dapplooker.com/browse/2/schema/moonbeam){target=_blank} and the [Moonriver Staking dashboards](https://analytics.dapplooker.com/browse/2/schema/moonriver){target=_blank}.

### Popular Dashboards {: #popular-dashboards }

- [Moonbeam Staking Dashboard](https://network.dapplooker.com/moonbeam/collator){target=_blank} - staking dashboards for collators and delegators on Moonbeam that includes APY data
- [Moonriver Staking Dashboard](https://network.dapplooker.com/moonriver/collator){target=_blank} - staking dashboards for collators and delegators on Moonriver that includes APY data
- [Dapplooker Explorer for Moonbeam](https://dapplooker.com/category/moonbeam?type=dashboard){target=_blank} - find popular dashboards on Moonbeam
- [Dapplooker Explorer for Moonriver](https://dapplooker.com/category/moonriver?type=dashboard){target=_blank} - find popular dashboards on Moonriver


--8<-- 'text/disclaimers/third-party-content.md'
---
ms.date: 01/13/2025
title: Set up SharePoint agents for pay-as-you-go billing
ms.reviewer:
ms.author: ruihu
author: maggierui
manager: jtremper
recommendations: true
audience: Admin
f1.keywords:
- NOCSH
ROBOTS: NOINDEX, NOFOLLOW
ms.topic: how-to
ms.service: sharepoint-online
ms.collection: 
- M365-collaboration
- m365copilot
- magic-ai-copilot
- Tier2
---
# Use agents with pay-as-you-go billing

## Set up SharePoint agents as an Azure resource

To use pay-as-you-go billing, you need to first set up SharePoint agents as a resource in Azure. That resource is used whenever a user without a Microsoft 365 Copilot license uses a SharePoint agent.

### Prerequisites to set up SharePoint agents as a resource in Azure

- Have at least a SharePoint administrator role
- Have Owner or Contributor Azure roles to a pay-as-you-go Azure subscription
- Have Owner or Contributor Azure roles to an Azure resource group linked to the same Azure subscription

> [!NOTE]
> - The Owner or Contributor Azure roles are only needed in the time windows where you set up billing.
> -	To grant an owner or Contributor Azure role, follow the instructions [here](/azure/role-based-access-control/role-assignments-portal). 


To set up SharePoint agents as an Azure resource, you need to do the following if you haven't already:

1. [Create an Azure subscription](https://azure.microsoft.com/pricing/offers/ms-azr-0003p/) with the pay-as-you-go offer. 
1. [Create an Azure resource group](/azure/azure-resource-manager/management/manage-resource-groups-portal#create-resource-groups) for SharePoint agents.

## Set up pay-as-you-go billing for SharePoint agents

After setting up an Azure resource group for SharePoint agents, you can set up pay-as-you-go billing for SharePoint agents in the Microsoft 365 admin center. Here's how:

1. Go to the Microsoft 365 admin center, select **Settings** then **Org settings** then select **pay-as-you-go** services (formerly Microsoft Syntex).
    Alternatively, you can select Setup, and then in the **Billing and licenses** section, select **Activate pay-as-you-go services**. On the **Activate pay-as-you-go services** page, select **Get started**.
1. On the **Pay-as-you-go services** page, under **Billing**, select **agents in SharePoint**.
1. On the **Set up billing and turn on services** panel, in the **Set up billing** section, under **Azure subscription**, select the dropdown, and then follow the steps to select the Azure subscription, resource group, and region. (The region determines where your tenant ID and usage information such as site names are stored.)
1. Read and accept the pay-as-you-go billing terms of service.
1. Select **Save**.


### Billing rates

The following table illustrates the differences in the subscription models for the cost of SharePoint agent usage.

| SharePoint agent feature              | Billing rate | Use in Microsoft 365 Copilot scenarios<sup>1</sup> | Autonomous use |
|---------------------------------------|--------------|----------------------------------------------------|----------------|
| Generative answer                     | 2 messages   | No charge                                          | 2 messages     |
| Tenant graph grounding for messages   | 10 messages  | No charge                                          | 10 messages    |

> [!NOTE]
> Each interaction with a SharePoint agent includes a question and an answer. The answer integrates the generative answer and the tenant graph grounding for messages. A successful interaction uses 12 messages.

### Monitor consumption in Microsoft Cost Management

To monitor your organization’s consumption of agents with the pay-as-you-go, you can create a budget in Microsoft Cost Management with [Bicep](/azure/cost-management-billing/costs/quick-create-budget-bicep) and [ARM template](/azure/cost-management-billing/costs/quick-create-budget-template). Budget helps you inform others about their spending to proactively manage costs and monitor how spending progresses over time. You can also set up various types of cost alerts to monitor the consumption. 
Furthermore, you can view your organization’s consumption by:

1. Going to [Microsoft Cost Management](https://portal.azure.com/#view/Microsoft_Azure_CostManagement/Menu/~/overview/openedBy/AzurePortal). 
1. If needed, change the scope to select the subscription that is being used for agents in SharePoint.

#### Adjusting consumption

Using pay-as-you-go billing means that each user is responsible for their own consumption. Work with people in your organization to ensure the efficient use of agents in SharePoint. For example, restrict access to SharePoint sites with agents to only those who need to use them.

### Paying your invoice

Your organization receives an invoice for all Azure services used at the end of each month. You can pay these invoices under the Invoices section in the subscription that you use for agents in SharePoint.

## Disconnect agents from pay-as-you-go billing

To Disconnect Agents from pay-as-you-go billing, follow these steps:

1. In the Microsoft 365 admin center, select **Settings** > **Org Settings**.
1. On the **Pay-as-you-go services** page, on the **Billing** tab, select **Agents in SharePoint**.
1. On the **Manage billing** panel, under the Azure Subscription, select **Edit billing information**.
1. Select **Disconnect Azure subscription** under **Manage Billing**.
1. Select **Disconnect** within the **Disconnect Subscription** pop-up window.
1. View confirmation that your Azure Subscription has been disconnected Under **set up billing and turn on services**. 

---
title: Ask your admin to create an environment for you when opening Copilot for Sales
description: Resolves the Ask your admin to create an environment for you error that occurs in Microsoft Copilot for Sales when a user tries to open the app.
ms.date: 04/19/2024
author: sbmjais
ms.author: shjais
ms.custom: sap:CRM Permissions and Configurations\CRM Settings
---
# "Ask your admin to create an environment for you" error when opening Microsoft Copilot for Sales

This article helps you resolve the "Ask your admin to create an environment for you" error in Microsoft Copilot for Sales when a user tries to open the app.

## Who is affected?

| Requirement type |Description  |
|---------|---------|
|**Client app**     |  Copilot for Sales Outlook add-in        |
|**Platform**     | Web and desktop clients         |
|**OS**     | Windows and Mac         |
|**Deployment**     | User managed and admin managed       |
|**CRM**     | Salesforce       |
|**Users**     | The first user who opens the app in the tenant.      |

## Symptoms

When a user tries to open Microsoft Copilot for Sales, the following error is displayed:

> Ask your admin to create an environment for you.

## Cause

This error occurs when the first user in a tenant tries to [open Microsoft Copilot for Sales](/microsoft-sales-copilot/open-app), and the tenant doesn't have any administrators assigned to create the environment.

## Resolution

To resolve this issue, assign at least one administrator to the tenant with your administrator credentials.

1. Open one of the following URLs as per your tenant type:

    - Production: [https://admin.powerplatform.microsoft.com/](https://admin.powerplatform.microsoft.com/)
    - Non-production: [https://admin.preprod.powerplatform.microsoft.com/](https://admin.preprod.powerplatform.microsoft.com/)

1. In the left pane, select **Admin centers** > **Microsoft Entra ID**.
1. In the left pane, select **Roles & admins** > **Roles & admins**.
1. Find the **Global Administrator** and **Power Platform Administrator** roles, and then assign the right users to the roles.

## More information

If your issue is still unresolved, go to the [Copilot for Sales - Microsoft Community Hub](https://techcommunity.microsoft.com/t5/viva-sales/bd-p/VivaSales) to engage with our experts.

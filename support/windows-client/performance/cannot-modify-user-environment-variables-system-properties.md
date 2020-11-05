---
title: can't modify user environment variables
description: Provides a resolution for the issue that you can't modify user environment variables in the System Properties dialog box.
ms.date: 10/09/2020
author: Deland-Han
ms.author: delhan 
manager: dscontentpm
audience: itpro
ms.topic: troubleshooting
ms.prod: windows-client
localization_priority: medium
ms.reviewer: kaushika
ms.prod-support-area-path: Performance monitoring tools
ms.technology: Performance
---
# You cannot modify user environment variables in the System Properties dialog box if you log on by using a standard user account

This article provides a resolution for the issue that you can't modify user environment variables in the System Properties dialog box.

_Original product version:_ &nbsp; Windows Vista  
_Original KB number:_ &nbsp; 931715

## Symptoms

If you log on by using a standard user account in Windows Vista, you can't modify user environment variables in the **System Properties** dialog box.

For example, if you try to access the System Properties dialog box by clicking **Advanced system settings** in the System item in Control Panel, you are prompted for administrator account credentials. If you type the credentials for an administrator account, the user environment variables that you can access are for that administrator account only.

## Cause

This issue occurs because of increased security in Windows Vista. The method that you must use to modify user environment variables in Windows Vista differs from earlier versions of Microsoft Windows.

## Resolution

To resolve this issue, modify the user environment variables by using the User Accounts item in Control Panel. You can follow these steps:

1. Click **Start**![Start button ](./media/cannot-modify-user-environment-variables-system-properties/vista-start-button.jpg), type Accounts in the **Start search** box, and then click **User Accounts** under **Programs**.

    ![User Account Control permission ](./media/cannot-modify-user-environment-variables-system-properties/security-shield.jpg) If you are prompted for an administrator password or for a confirmation, type the password, or click **Allow**.
2. In the **User Accounts** dialog box, click **Change my environment variables** under **Tasks**.

3. Make the changes that you want to the user environment variables for your user account, and then click **OK**.
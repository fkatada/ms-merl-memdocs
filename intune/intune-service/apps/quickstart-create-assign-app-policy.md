---
# required metadata

title: Create and assign an app protection policy
titleSuffix: Microsoft Intune
description: In this article, you use Microsoft Intune to create and assign and app protection policy.
keywords:
author: nicholasswhite
ms.author: nwhite
manager: laurawi
ms.topic: how-to
ms.date: 02/28/2025
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.assetid: 2586fce0-5dca-4686-b9c4-791778838401

# optional metadata

#ROBOTS:
#audience:

ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection:
- tier2
- M365-identity-device-management
- FocusArea_Apps_Protect
---

# Step 9: Create and assign an app protection policy

In this article, you use Intune to create and assign an app protection policy to a client app on an end user's device. Intune uses app protection policies to confirm that your apps are meeting your organization's data protection requirements.

[!INCLUDE [intune-evaluate](../includes/intune-evaluate.md)]

If you don't have an Intune subscription, [sign up for a free trial account](../fundamentals/free-trial-sign-up.md).

## Prerequisites

- To complete this evaluation step, you must [create a user](../fundamentals/quickstart-create-user.md), [create a group](../fundamentals/quickstart-create-group.md), [enroll a device](../enrollment/quickstart-setup-auto-enrollment.md), and [add and assign an app](quickstart-add-assign-app.md).

## Sign in to Intune

Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) as an [Intune administrator](../fundamentals/role-based-access-control-reference.md) with sufficient permissions. If you have created an Intune Trial subscription, the account you created the subscription with is a Microsoft Entra [Global administrator](/entra/identity/role-based-access-control/permissions-reference#global-administrator).

> [!CAUTION]  
> The Global Administrator built-in role is a [privileged Microsoft Entra ID role](/entra/identity/role-based-access-control/privileged-roles-permissions?tabs=admin-center), and isn’t recommended for daily use. As described the [sign-in to Intune artice](../fundamentals/account-sign-up.md#role-based-access-controls), you can reduce reliance on this role by assigning a less-privileged role to administrators who manage Intune and perform daily tasks.

## Create an app protection policy

Use the following steps to create an app protection policy:

1. In [Intune](https://aka.ms/intuneportal), select **Apps** > **Protection** > **Create** > **Windows 10**.
2. Enter the following details:

    - **Name**: *Windows 10 content protection*
    - **Description**: *Users associated with this policy won't be able to cut, copy, or paste any content between the assigned app and other nonmanaged apps on the device.*
    - **Enrollment state**: *With enrollment*

3. Under **Protected apps**, select **Add**. The **Add apps** pane is displayed.
4. Choose the apps that must adhere to this policy and select **OK**.
5. Select **Next** to display the **Required settings**.
6. Select **Allow Overrides** to set the Windows Information Protection mode. Selecting this option blocks enterprise data from leaving the protected app.
7. Select **Next** to display the **Advanced settings**.
8. Select **Next** to display the **Assignments**.
9. Select **Select groups to include**, select the group, and select **Select**.
10. Select **Next** to display the **Review + create** step.
11. Select **Create** to create your policy.

You see the app protection policy in Intune.

> [!NOTE]
> App protection policies can only be applied to groups that contain users, not groups that contain devices.

## Next steps

In this article, you created and assigned an app protection policy. Users of the app that have this policy assigned won't be able to cut, copy, or paste any content between the assigned app and other nonmanaged apps on the device. This type of protection helps protect your organization's data. For more information about app protection policies in Intune, see [What are app protection policies?](app-protection-policy.md)

To continue to evaluate Microsoft Intune, go to the next step:

> [!div class="nextstepaction"]
> [Step 10: Create and assign a custom role](../fundamentals/quickstart-create-custom-role.md)

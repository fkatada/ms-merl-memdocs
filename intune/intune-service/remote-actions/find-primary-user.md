---
# required metadata

title: Find the primary user of a Microsoft Intune device.
titleSuffix:
description: Find the primary user (or User Device Affinity) of an Intune device.
keywords:
author: Smritib17
ms.author: smbhardwaj
manager: dougeby
ms.date: 02/28/2025
ms.topic: how-to
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high

# optional metadata

#ROBOTS:
#audience:

ms.reviewer:
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection:
- tier2
- M365-identity-device-management
---

# Find the primary user of an Intune device

Primary user, also known as User Device Affinity, is a property of each Intune device.
An Intune device can have zero or one primary user assigned to it. When there's no primary user assigned, the device is referred to as a "Shared Device".

## Find a device's primary user

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Choose **Devices** > choose a device.
3. On the **Overview** page, you can see the primary user listed.

## Change a device's primary user

For Windows 10 devices that are Microsoft Entra joined or Microsoft Entra hybrid joined, the primary user of a device can be updated.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Choose **Devices** > **All devices** > choose a Windows device > **Properties** > **Change primary user**.
3. Select a new user and choose **Select**.

After the primary user is updated, it will also be updated in Intune and Microsoft Entra device blades.

>[!NOTE]
>- Supported on Windows devices only. Enrollment is required to assign a new primary user on iOS and Android devices.
>- Supported on Microsoft Entra joined and Microsoft Entra hybrid joined devices only. Not supported on devices that are Microsoft Entra registered only.
>- To be assigned as the Primary user, the user must be licensed for Intune.
>- Updates to the primary user across Intune and Microsoft Entra ID can take up to 10 minutes to be reflected.
>- Changing the primary user of the device doesn't make any changes to local group membership such as adding or removing users from the "Administrators" local group.
>- Changing the primary user doesn't change the "Enrolled by" user in Intune.
>- To change or remove the Primary user of a device, you require the permission **Managed devices/Set primary user**.

## What is the primary user?

The primary user property is used to map a licensed Intune user to their devices in:

- The Company Portal app
- End-user website
- IT pro experiences, like troubleshooting pages in the Azure portal. These pages map user accounts to devices by using the primary user.

### Company Portal app

The Company Portal app expects that the user account that signed in to the Company Portal is the primary user of that device. If you assign another user as the primary user, the Company Portal shows a warning:

"This device is already assigned to someone in your organization. Contact company support about becoming the primary device user. You can continue to use Company Portal but functionality is limited."

If an Intune device has no primary user assigned, then the Company Portal app detects it as a shared device. Shared devices are visually identifiable with a "shared" label appearing on the device tile. In this mode, the Company Portal can still be used to request and install available apps. However, uninstalling apps and self-service actions (reset/rename/retire) aren't available.

To appear in the Company Portal on shared devices, available apps may be assigned to the device or user. They are installed in the system context or user context, depending on how the app was configured by the IT administrator. For more information about app context, see [Installing apps on Windows 10 devices](../apps/apps-windows-10-app-deploy.md). Company Portal version 10.3.4651.0 or later is required to use this feature.

## Who is assigned as the primary user?

Intune automatically adds primary user to devices during or soon after enrollment. The enrollment method determines when the primary user is added to a device.

| Platform | Enrollment method | Primary user assigned | Primary user is assigned |
| ---- | ---- | ---- | ---- |
| Windows | Add work or school (user driven) | Enrolling user | During enrollment |
| Windows | Modern App sign-in (user driven) | Enrolling user | During enrollment |
| Windows | Enroll in mobile device management (MDM) only (user driven) | Enrolling user | During enrollment |
| Windows | Microsoft Entra join (out of box experience) | Enrolling user | During enrollment |
| Windows | Microsoft Entra join (Windows Autopilot out of box experience) | Enrolling user | During enrollment |
| Windows | Enroll in MDM only | Enrolling user | During enrollment |
| Windows | Microsoft Entra hybrid join + automatic enrollment GPO | First user to sign in to Windows | When first user signs in to Windows|
| Windows | Co-management | First user to sign in to Windows | When first user signs in to Windows |
| Windows | Microsoft Entra join (bulk enrollment token) | None | Not applicable |
| Windows | Microsoft Entra join (Windows Autopilot self-deploying mode) | None | Not applicable |
| Cross-platform | User driven enrollment with Company Portal App | Enrolling user | During enrollment |
| Cross-platform | Device Enrollment Manager (DEM) | Enrolling DEM user | During enrollment |
| iOS/iPadOS, macOS | Apple Automated Device Enrollment (DEP with User Affinity) | Enrolling user | During enrollment |
| iOS/iPadOS, macOS | Apple Automated Device Enrollment (DEP without User Affinity) | None | Not applicable |
| Android | Android Corporate-Owned, Dedicated devices | None | Not applicable |

## Primary user and Microsoft Entra device owner

In some cases, the Intune primary user can be different from the Microsoft Entra Device's **Owner** property (viewable under **Devices** > **Microsoft Entra Devices**). The Microsoft Entra Device owner is added during a device's registration into Microsoft Entra ID.

For newly enrolled Microsoft Entra devices, the Microsoft Entra ID **Owner** property is automatically set at the same time that the Intune primary user is set.

## Next steps

[Manage your Intune devices.](device-management.md)

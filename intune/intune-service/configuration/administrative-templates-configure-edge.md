---
title: Deploy Microsoft Edge policy using ADMX template in Microsoft Intune
description: Add or create settings using ADMX administrative templates to configure Microsoft Edge on Windows devices. Using Microsoft Intune, you can configure group policy settings, and deploy these settings to Microsoft Edge users.
ms.author: mandia
author: MandiOhlinger
manager: laurawi
ms.date: 07/22/2024
audience: ITPro
ms.topic: how-to
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high

# optional metadata

#ROBOTS:

ms.reviewer: mikedano
ms.suite: ems
ms.custom: intune-azure
ms.collection:
- tier2
- M365-identity-device-management
---

# Configure Microsoft Edge policy settings in Microsoft Intune

Using Administrative Templates in Microsoft Intune, you can create and manage Microsoft Edge policy settings on your Windows client devices. Administrative Templates use the ADMX templates for Microsoft Edge.

For example, you can:

- Allow specific extensions
- Add download restrictions
- Use autofill
- Show the favorites bar
- And more...

These settings are created in an Intune policy, and then deployed to Windows client devices in your organization.

This article applies to:

- Windows 11
- Windows 10
- Microsoft Edge version 77 and newer

  For Microsoft Edge version 45 and earlier, go to [Microsoft Edge Browser device restrictions](device-restrictions-windows-10.md#microsoft-edge-legacy-version-45-and-older).

> [!NOTE]
> Additional ADMX settings for Edge 96 and Edge updater have been added to Administrative Templates. The additional settings include support for **Target Channel override**. **Target Channel override** allows customers to opt into the **[Extended Stable](https://blogs.windows.com/msedgedev/2021/07/15/opt-in-extended-stable-release-cycle/)** release cycle option at any point using Group Policy or through Intune.

When you use Intune to manage and enforce ADMX policies, the process is similar to using Active Directory group policy. Or, similar to configuring local Group Policy Object (GPO) settings on user devices. For more information on ADMX policies in Intune, go to [Use Windows 10/11 templates to configure group policy settings in Microsoft Intune](administrative-templates-windows.md).

This article shows you how to configure Microsoft Edge policy settings using administrative templates in Microsoft Intune.

You can also use the [Intune settings catalog](settings-catalog.md) to configure Microsoft Edge for Windows and macOS devices. To learn more about the settings catalog, go to [Use the settings catalog to configure settings in Microsoft Intune](settings-catalog.md).

> [!TIP]
>
> - For information on adding the Microsoft Edge version 77+ app on Windows client, go to [Add Edge app on Windows client devices](../apps/apps-windows-edge.md).
> - For information on adding and configuring Microsoft Edge version 77+ app on macOS, go to [Add Edge app](../apps/apps-edge-macos.md), and [Configure Edge app using plist](/DeployEdge/configure-microsoft-edge-on-mac).
> - For a list of the Microsoft Edge updates, including new policies, go to the [Release notes for Microsoft Edge](/deployedge/microsoft-edge-relnote-stable-channel#policy-updates).

## Prerequisites

- To configure the ADMX policy, at a minimum, sign into the Intune admin center with the **Policy and Profile manager** role. For information on the built-in roles in Intune, and what they can do, go to [Role-based access control (RBAC) with Microsoft Intune](../fundamentals/role-based-access-control.md).

- Wi-Fi profiles support the following device platforms:

  - Windows 11
  - Windows 10 with the following minimum system requirements:

    - Windows 10, version 1909
    - Windows 10, version 1903 with [KB4512941](https://support.microsoft.com/kb/4512941) installed
    - Windows 10, version 1809 with [KB4512534](https://support.microsoft.com/kb/4512534) installed
    - Windows 10, version 1803 with [KB4512509](https://support.microsoft.com/kb/4512509) installed
    - Windows 10, version 1709 with [KB4516071](https://support.microsoft.com/kb/4516071) installed

## Create a policy for Microsoft Edge

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Manage devices** > **Configuration** > **Create** > **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Templates** > **Administrative Templates**.

4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **ADMX: Configure Edge on Windows 10/11 devices**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.

    Your properties look similar to the following properties:

    :::image type="content" source="./media/administrative-templates-configure-edge/create-windows-administrative-template.png" alt-text="Create a Windows ADMX administrative template in Microsoft Intune and Intune admin center.":::

6. Select **Next**.

7. In **Configuration settings**, the Microsoft Edge settings are available in **Computer configuration** and **User configuration**. Microsoft Edge is shown:

   - **Computer configuration**: Settings apply to the computer, even if no one is signed in.
   - **User configuration**: Settings apply to all users signed in to the device.

    :::image type="content" source="./media/administrative-templates-configure-edge/all-settings-computer-configuration-user-configuration.png" alt-text="Screenshot that shows the ADMX settings for user configuration and computer configuration in Microsoft Intune and Intune admin center.":::

8. Select **Computer Configuration** > **Microsoft Edge** > **Allow download restrictions**. The policy description and values are shown:

    :::image type="content" source="./media/administrative-templates-configure-edge/allow-download-restrictions-microsoft-edge.png" alt-text="Screenshot of Select Microsoft Edge ADMX template and select a sample setting in Microsoft Intune and Intune admin center.":::

   > [!NOTE]
   > For a list of the available settings, go to [Microsoft Edge – Policies](/DeployEdge/microsoft-edge-policies) and [Microsoft Edge – Update policies](/DeployEdge/microsoft-edge-update-policies).

9. Close the policy description. Use search to find a specific setting you want to configure. For example, search for "home page":

    :::image type="content" source="./media/administrative-templates-configure-edge/search-home-page-microsoft-edge.png" alt-text="Screenshot of Use the search to filter ADMX settings in Microsoft Intune and Intune admin center.":::

10. Select **Configure the home page URL** > **Enabled**, and set its value to `https://www.bing.com`:

    :::image type="content" source="./media/administrative-templates-configure-edge/set-home-page-url-microsoft-edge.png" alt-text="Screenshot of Set the Microsoft Edge home page URL to a web site using ADMX templates in Microsoft Intune and Intune admin center.":::

11. Select **OK**. The **State** now shows **Enabled**:

    :::image type="content" source="./media/administrative-templates-configure-edge/state-enabled.png" alt-text="Screenshot of When you configure an ADMX setting, the state shows enabled in Microsoft Intune and Intune admin center.":::

12. Select **Next**. In **Scope tags**, select **Next**.

    Scope tags are optional, and this example doesn't use them. To learn more about scope tags, and what they do, go to [Use role-based access control (RBAC) and scope tags for distributed IT](../fundamentals/scope-tags.md).

13. In **Assignments**, select **Next**.

    Assignments are optional, and this example doesn't use them. In production, select **Add groups**. Select a Microsoft Entra group that includes users or devices that should receive this policy. For information and guidance on assigning policies, go to [Assign user and device profiles in Intune](device-profile-assign.md).

    :::image type="content" source="./media/administrative-templates-configure-edge/add-entra-group-assign-policy.png" alt-text="Screenshot of Assign or deploy the ADMX policy template to users or groups in Microsoft Intune and Intune admin center.":::

14. In **Review + create**, the summary of your changes is shown. Select **Create**.

    When you create the profile, your policy is automatically assigned to the users or groups you chose. If you didn't choose any users or groups, then your policy is created, but it isn't deployed.

    Your new Microsoft Edge policy is shown in the list:

    :::image type="content" source="./media/administrative-templates-configure-edge/saved-profile.png" alt-text="Screenshot of the ADMX policy setting is shown in the device configuration profile list in Microsoft Intune and Intune admin center.":::

For more information about ADMX administrative templates, go to:

- [Use Windows 10/11 templates to configure group policy settings in Microsoft Intune](administrative-templates-windows.md).
- [Tutorial: Use the cloud to configure group policy on Windows client devices with ADMX templates and Microsoft Intune](tutorial-walkthrough-administrative-templates.md)

## Related content

- [Download Microsoft Edge for your business](https://aka.ms/EdgeEnterprise)
- [Manage web access by using Microsoft Edge with Microsoft Intune](../apps/manage-microsoft-edge.md)
- [Use Windows 10/11 templates to configure group policy settings in Microsoft Intune](administrative-templates-windows.md)
- [Deploy Microsoft Edge app using Microsoft Intune](../apps/apps-windows-edge.md)

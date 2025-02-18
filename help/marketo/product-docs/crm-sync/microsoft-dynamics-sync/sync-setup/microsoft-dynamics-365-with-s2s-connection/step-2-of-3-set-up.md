---
unique-page-id: 3571827
description: Step 2 of 3 - Set up the Marketo Solution with Server to Server Connection - Marketo Docs - Product Documentation
title: Step 2 of 3 - Set up the Marketo Solution with Server to Server Connection
exl-id: 324e2142-2aa2-4548-9a04-683832e3ba69
---
# Step 2 of 3: Set up Marketo Solution with Server to Server Connection {#step-2-of-3-set-up-marketo-sync-user-in-dynamics-s2s}

>[!PREREQUISITES]
>
>[Step 1 of 3: Install the Marketo Solution with Server to Server Connection](/help/marketo/product-docs/crm-sync/microsoft-dynamics-sync/sync-setup/microsoft-dynamics-365-with-s2s-connection/step-1-of-3-install.md)

## Create Client Application in Azure AD {#create-client-application-in-azure-ad}

1. Navigate to [this Microsoft article](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory#create-an-application-registration).

1. Follow all the steps. For Step 3, enter a relevant application name (e.g., "Marketo Integration"). Under the Supported Account Types, select **Account in this Organizational Directory Only**.

1. Write down the Application ID (ClientId) and Tenant ID. You'll need to  enter it in Marketo later.

1. Grant Admin consent by following the steps [in this article](/help/marketo/product-docs/crm-sync/microsoft-dynamics-sync/sync-setup/grant-consent-for-client-id-and-app-registration.md).

1. Generate a Client Secret in the Admin Center by clicking **Certificates & secrets**.

   ![](assets/step-2-of-3-set-up-marketo-sync-user-in-dynamics-s2s-1.png)

1. Click the **New client secret** button.

   ![](assets/step-2-of-3-set-up-marketo-sync-user-in-dynamics-s2s-2.png)

1. Enter a client secret description and click **Add**.

   ![](assets/step-2-of-3-set-up-marketo-sync-user-in-dynamics-s2s-3.png)

>[!CAUTION]
>
>Make sure to make note of the Client Secret value (seen in the screenshot below), as you'll need it later. It is only shown once, and you won't be able to retrieve it again.

   ![](assets/step-2-of-3-set-up-marketo-sync-user-in-dynamics-s2s-4.png)

1. Follow steps from the following link to [set up an application user in  Microsoft](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/use-single-tenant-server-server-authentication#application-user-creation). While giving permissions to the Application User, assign it to "Marketo  Sync User Role."

## Azure AD Federated with AD FS On-prem {#azure-ad-federated-with-ad-fs-on-prem}

Federated Azure AD to ADFS Onprem needs the creation of a Home Realm Discovery policy for the specific application. With this policy, Azure AD will redirect the authentication request to the federation service. Password hash synchronization has to be enabled in AD Connect for this. For more information, please see [OAuth with ROPC](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth-ropc) and [Set an hrd policy for an application](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/configure-authentication-for-federated-users-portal#example-set-an-hrd-policy-for-an-application).

Additional references [can be found here](https://docs.microsoft.com/en-us/azure/active-directory/reports-monitoring/concept-all-sign-ins#:~:text=Interactive%20user%20sign%2Dins%20are,as%20the%20Microsoft%20Authenticator%20app.&text=This%20report%20also%20includes%20federated,are%20federated%20to%20Azure%20AD.).

## Assign Sync User Role {#assign-sync-user-role}

1. Assign the Marketo Sync User role to the Marketo sync user only.

>[!NOTE]
>
>This applies to Marketo version 4.0.0.14 and later. For earlier versions, all users must have the sync user role. To upgrade your Marketo solution, [see this article](/help/marketo/product-docs/crm-sync/microsoft-dynamics-sync/sync-setup/update-the-marketo-solution-for-microsoft-dynamics.md).

1. Go back to the Application Users tab and refresh the users list.

   ![](assets/step-2-of-3-set-up-marketo-sync-user-in-dynamics-s2s-5.png)

1. Hover next to the newly created  Application  user, and a checkbox will appear. Click to select it.

   ![](assets/step-2-of-3-set-up-marketo-sync-user-in-dynamics-s2s-6.png)

1. Click **Manage Roles**.

   ![](assets/step-2-of-3-set-up-marketo-sync-user-in-dynamics-s2s-7.png)

1. Check **Marketo Sync User** and click **OK**.

   ![](assets/step-2-of-3-set-up-marketo-sync-user-in-dynamics-s2s-8.png)

## Configure Marketo Solution {#configure-marketo-solution}

Almost there! All we have left is to inform Marketo Solution about the new user created.

>[!IMPORTANT]
>
>If you’re upgrading from Basic Authentication to OAuth, you’ll need to contact [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support) for help with updating the additional parameters. Enabling this feature will temporarily stop the sync until new credentials are entered and the sync is re-enabled. The feature can be disabled (until April 2022) should you want to revert to the old Authentication mode.

1. Go back to the Advanced Settings section and click the ![](assets/image2015-5-13-15-3a49-3a19.png) icon next to Settings, and select **Marketo Config**.

   ![](assets/fourteen.png)

   >[!NOTE]
   >
   >If you don't see **Marketo Config** in the Settings menu, refresh the page. If that doesn't work, try to [publish the Marketo Solution](/help/marketo/product-docs/crm-sync/microsoft-dynamics-sync/sync-setup/microsoft-dynamics-365-with-s2s-connection/step-1-of-3-install.md) again or log out and back in.

1. Click **Default**.

   ![](assets/fifteen.png)

1. Click the search button on the **Marketo User** field and select the sync user you created.

   ![](assets/sixteen.png)

1. Click the ![](assets/image2015-3-13-15-3a10-3a11.png) icon in the bottom-right corner to save the changes.

   ![](assets/image2015-3-13-15-3a3-3a3.png)

1. Click the **X** in the upper-right to close the screen.

   ![](assets/seventeen.png)

1. Click the ![](assets/image2015-5-13-15-3a49-3a19-1.png) icon next to Settings, and select **Solutions**.

   ![](assets/eighteen.png)

1. Click the **Publish All Customizations** button.

   ![](assets/nineteen.png)

## Before Proceeding to Step 3 {#before-proceeding-to-step}

* If you want to restrict the number of records you sync, [set up a custom sync filter](/help/marketo/product-docs/crm-sync/microsoft-dynamics-sync/create-a-custom-dynamics-sync-filter.md) now.
* Run the [Validate Microsoft Dynamics Sync](/help/marketo/product-docs/crm-sync/microsoft-dynamics-sync/sync-setup/validate-microsoft-dynamics-sync.md) process. It verifies that your initial setups were done correctly.
* Log in to the Marketo Sync User in Microsoft Dynamics CRM.

>[!MORELIKETHIS]
>
>[Step 3 of 3: Connect the Marketo Solution with Server to Server Connection](/help/marketo/product-docs/crm-sync/microsoft-dynamics-sync/sync-setup/microsoft-dynamics-365-with-s2s-connection/step-3-of-3-connect.md)

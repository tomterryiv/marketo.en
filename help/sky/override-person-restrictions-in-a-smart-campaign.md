---
title: override-person-restrictions-in-a-smart-campaign
description: Override Person Restrictions in a Smart Campaign
exl-id: efdd6c68-a95e-4b2a-9249-e2e1f550b628
---
# Override Person Restrictions in a Smart Campaign

<br>&nbsp;

Marketo allows you to set the maximum number of people that can qualify for a smart campaign; this helps you avoid accidentally emailing your whole database. If you want to override this limit, here's how.

>[!IMPORTANT]
>
>Be sure to [enable person restrictions for smart campaigns](https://docs.marketo.com/display/DOCS/Enable+Person+Restrictions+for+Smart+Campaigns) in Marketo [!UICONTROL Admin].

1. Find your smart campaign and click **[!UICONTROL Schedule]**.

   ![Image One](/help/sky/assets/smart-campaigns/override-person-restrictions-in-a-smart-campaign/override-person-restrictions-in-a-smart-campaign-1.png)

1. Click **[!UICONTROL Qualification Rules]**.

   ![Image Two](/help/sky/assets/smart-campaigns/override-person-restrictions-in-a-smart-campaign/override-person-restrictions-in-a-smart-campaign-2.png)

   >[!NOTE]
   >
   >The default limit is the one set in Admin.

1. Next to **[!UICONTROL Abort campaign if qualified leads exceed]**, enter a new limit.

   ![Image Three](/help/sky/assets/smart-campaigns/override-person-restrictions-in-a-smart-campaign/override-person-restrictions-in-a-smart-campaign-3.png)

>[!NOTE]
>
>The smart campaign will not run if the number of people who qualify exceed the set limit.

>[!CAUTION]
>
>Be careful with this feature so that you don't accidentally include too many people.

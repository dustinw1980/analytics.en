---
description: Learn about the benefits and constraints of using Timestamps Optional setting.
keywords: Analytics Implementation
seo-description: Learn about the benefits and constraints of using Timestamps Optional setting.
seo-title: Using Timestamps Optional
solution: Analytics
title: Using Timestamps Optional
topic: Developer and implementation
uuid: 956aaa16-6ffa-4b63-b022-a659f5143e00
index: y
internal: n
snippet: y
---

# Using Timestamps Optional

Learn about the benefits and constraints of using Timestamps Optional setting.

Timestamps Optional is the default setting for all new report suites.

* Mix timestamped and non-timestamped data in the same global report suite. 
* Send timestamped data from a mobile app to a global report suite. 
* Upgrade apps to employ timestamps without having to create a new report suite.

>[!NOTE]
>
>Timestamps Optional is the default setting for all new report suites generated from a template. New report suites copied from an existing report suite will inherit settings from the original.

See [Timestamps Optional](https://marketing.adobe.com/resources/help/en_US/reference/timestamp-optional.html) for additional setup information.

## Timestamps Optional: Integrating Timestamped and Non-timestamped Data {#section_BF17CB593044462B993FD0D28EA56518}

Using the Timestamps Optional feature, you can combine non-timestamped data with timestamped data without incurring data loss. Offline data with timestamps generated from a mobile device can be combined with live, non-timestamped data from a web page—or integrated with data from any platform using a client-side timestamp call.

* **Timestamp data**. Client-side timestamp data is captured and sent directly with the device data using client-side timestamp variables: Javascript ( [ [!DNL s.timestamp]](timestamp.md#concept_D997A2FF4D134C80A614C0BC7A4D7507)) on a web page, or using a Mobile SDK call ( [!DNL offlineEnabled=true]) in a mobile app. 
* **Non-timestamp data**. Adobe sets a timestamp on non-timestamped data in a report suite when the data hits the collection servers.

![](assets/timestamp_v_non2.png)

A report suite can have one of the following timestamp settings:

* Timestamps not allowed (setting visitorID supported) 
* Timestamps required (setting visitorID not supported) 
* Timestamps optional (setting visitorID supported but not on timestamped hits)

## About Timestamps Optional Features {#section_63B2FA9A2AB24B3993E84D2C2B4BF2CE}

Timestamps Optional allows you to integrate and report across multiple report suites with or without client-side timestamps included. With Timestamps Optional you can update your app to employ timestamps while still using non-timestamped data from the previous app. 

<table id="table_DF81590139424E6B8E06003AE5336D9D"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> In previous releases... </th> 
   <th colname="col2" class="entry"> In addition... </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Timestamped data could not be sent to a non-timestamped global report suite. Consequently, hit data sent from offline devices was dropped when adding to a non-timestamped report suite. </p> <img placement="break" align="center" href="assets/timestamp_v_non4_1.png" id="image_A23F1BE4E52B4752BB6141138846FCE6" /> <p>Consequently, hit data sent from offline data was dropped when adding to a non-timestamped report suite. </p> </td> 
   <td colname="col2"> <p>Updating an app to collect and use timestamps required you to employ a new report suite. </p> <img placement="break" align="center" href="assets/timestamp_v_non4_2.png" id="image_6BC3F3E1C85A4615A61E7F3256793A7B" /> <p></p> <p>You could not save to the existing report suite or integrate existing data when updating your app to use timestamps. </p> </td> 
  </tr> 
 </tbody> 
</table>

**With Timestamps Optional**, you can integrate non-timestamped data from a live website with offline data from mobile devices, or update your non-timestamped app to a timestamped app. ![](assets/timestamp_v_non6.png)

## Combining Data into a Global Report Suite {#section_5BE3BDF56007402BB1F5C3144D5FE1E0}

Combining data into a global report suite can be done in multiple ways, including multi-suite tagging, Vista rules, and imported batch files from offline sources. 

![](assets/timestamp_v_non9.png)

>[!IMPORTANT]
>
>Carefully plan the design for each component data set so the combination makes sense in a global report suite.

## Best Practices when Employing Timestamps {#section_9436394E5D7E4F8A8B369B6D11BB2B2B}

The following are best practices and a few requirements and restrictions to be aware of when integrating timestamped with non-timestamped data.

* In general, timestamps for a given visitor or visit must arrive at Adobe in the correct chronological order.

  Out-of-order data can include late arriving data from offline data collection and late arriving hits, or out-of-sync clocks on offline mobile devices. Out-of-order data can negatively impact time calculations (such as time spent values), attribution (eVar persistence), visit number/visit counts, and pathing reports. 

  ![](assets/timestamp_v_non8.png)

* Using timestamps when setting a [s.visitorID](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom) is not recommended. It can lead to out-of-order data.

* Hybrid apps composed of an app (timestamped, offline data) opening a web browser (non-timestamped, live data) should not use timestamps. It results in inaccurate reporting of the session. 

  ![](assets/timestamp_v_non.png)

  In addition, hybrid apps should not set a visitor ID.
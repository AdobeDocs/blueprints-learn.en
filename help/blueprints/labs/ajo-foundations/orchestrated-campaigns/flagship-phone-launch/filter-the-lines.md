---
title: Filter the lines
description: Learn how to filter out opted-out customer lines with a Split activity and use Change Dimension to align a workflow's target dimension with the SMS channel configuration.
doc-type: article
solution: Experience Platform
exl-id: fb556a27-5c73-4457-ae98-dba43d445c7f
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
---

# Filter the lines

## Objective

In the next set of steps you are going to filter out all the lines that are actually not allowed to be targeted with an SMS message due to their opting out at the line level.  You can not rely here on Profile consent because this is a line level target.



## Set up Split activity

1. Click the **+** icon on the bottom transition of the Fork activity and select the **Split** activity on the popup. 

   ![Add a Split activity to the bottom fork branch](assets/filter-the-lines-add-split-activity.png)



2. In the right rail update the Label to state the following:  `Filter out opt'd out lines`

   ![Split activity label set to Filter out opt'd out lines](assets/filter-the-lines-set-split-label.png)



3. In the right rail expand the default segment **Subset** section and click the **Create filter** button

   ![Create filter button in the Subset section](assets/filter-the-lines-create-filter-button.png)



4. Add a condition to ensure that you remove all Customer Lines that are opt'd out of SMS messaging and then click **Confirm**.

   ![Condition removing Customer Lines opted out of SMS](assets/filter-the-lines-sms-optin-condition.png)

   >[!NOTE]
   >
   >You need to figure out how to create the condition but the final result matches the screenshot above.  You got this!



5. Click the Save button in the upper right to save your work.  Your canvas looks like so now\...

![Workflow canvas after saving the split activity](assets/filter-the-lines-canvas-after-split-save.png)



## Add the SMS activity

1. On the workflow canvas, click the **+** icon after the split condition you added and select the **Mobile message Activity**

   ![Add the Mobile message activity after the split condition](assets/filter-the-lines-add-sms-activity.png)

   ![SMS activity added to the workflow canvas](assets/filter-the-lines-sms-activity-on-canvas.png)



2. In the right rail click on the Edit Mobile message button to start configuration of the SMS message

   ![Edit Mobile message button in the right rail](assets/filter-the-lines-edit-sms-button.png)



3. In the top nav click on the Actions menu item and then from the Mobile message configuration drop-down select the channel you previously created.

![SMS configuration successfully showing the selected channel](assets/filter-the-lines-sms-configuration-selected.png)




## Recap

You filtered out all the lines that were not allowed to be targeted with an SMS message due to opt out and you added an SMS activity for those who were allowed to be targeted.

---
title: Verification and validation
description: Preview a streamed dataset in the UI and run SQL queries to verify ingested records and nested schema fields.
doc-type: article
solution: Experience Platform
exl-id: fbdb0b6b-08b6-49b8-b6ab-d59d5941c678
---

# Preview the Dataset

1. Click on** Datasets**
1. **Locate **and **click **the dataset name that you created.

![Access the dataset in the datasets pane.png "Access the dataset in the Datasets pane"](assets/kILMiHMvCQfwD4tfXN7x0_access-the-dataset-in-the-datasets-pane.png "Access the dataset in the Datasets pane")



3\. Click on **Preview dataset **in the top right corner

![LxxLyKc0x1oi fRK2zloBczpXHnXIo055v 20241025 014953.png "Preview dataset is in the top right corner "](assets/n-ADAXZy_lxxLyKc0x1oi-fRK2zloBczpXHnXIo055v-20241025-014953.png "Preview dataset is in the top right corner ")



4\. **Verify** and** validate **the same records that you ingested by clicking on the left pane showing the schema hierarchy.

![YZt verify and validate the dataset.png "Verify and validate the dataset"](assets/RbTsCCfcTm2pp4y6G_yZt_verify-and-validate-the-dataset.png "Verify and validate the dataset")

>[!NOTE]
>
>**Preview dataset **will only show the first few rows of the dataset. Array objects are not viewable. 



## Query Dataset

1. **Close **the Preview
1. In the Dataset screen, click the copy icon on **Table name**. In the example screen below, the table name is `customer_account_sm`

![Copy the table name verification and validation.png "Copy the table name"](assets/ZNyTVVQKYtOTDzwmEGG66_copy-the-table-name-verification-and-validation.png "Copy the table name")



3\. Navigate to **Queries **section 

4\. Click on **Create query**

![Access the query editor.png "Access the query editor"](assets/y8iZAGPEMMupxqjIUTcRp_access-the-query-editor.png "Access the query editor")



5\. Turn the toggle for **Enhanced Query Editor**

![LxxLyKc0x1oi KP9dkIS0qnNkivWSi1Vjm 20241025 015607.png "Query editor interface"](assets/n-ADAXZy_lxxLyKc0x1oi-KP9dkIS0qnNkivWSi1Vjm-20241025-015607.png "Query editor interface")



6\. Copy paste the following SQL query in the** Editor**. Remember to replace `<table_name>` with the value you obtained in step 6.

```sql
SELECT * FROM <table_name>
```



7\. Press the** Play **button. 

8.** Preview **the results. 

9\. Also, execute the following SQL query to retrieve the XDM schema along with the data:

```sql
SELECT to_json(shippingAddress) FROM <table_name>
```



10\. To access the data in the `postalCode`** node**`,` you can type:

```sql
SELECT shippingAddress.postalCode FROM <table_name>
```

>[!TIP]
>
>Congratulations!  You have successfully ingested and created a sample set of Real-Time Customer Profiles


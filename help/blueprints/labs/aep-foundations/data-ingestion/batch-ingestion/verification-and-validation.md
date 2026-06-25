---
title: Verification and Validation
description: Verification and Validation
doc-type: article
solution: Experience Platform
exl-id: 7e7cd43d-cc24-4a40-a175-2c651436ab79
---

# Preview the Dataset

1. Click on** Datasets**
1. **Locate **and **click **the dataset name that you created.

![Access the dataset in the datasets pane.png "Access the dataset in the Datasets pane"](assets/hrf-PK5SbKm6lzh8DVqd5_access-the-dataset-in-the-datasets-pane.png "Access the dataset in the Datasets pane")



3\. Click on **Preview dataset **in the top right corner

![Preview dataset is in the top right cornerverification and validation.png "Preview dataset is in the top right corner"](assets/iuAD5bK3hAX5xjkY5ncPO_preview-dataset-is-in-the-top-right-cornerverification-and-validation.png "Preview dataset is in the top right corner")



4\. **Verify** and** validate **the same records that you ingested by clicking on the left pane showing the schema hierarchy.

![Verify and validate the dataset](assets/HoaBW4lMW5bRCQCNVzlqJ_verify-and-validate-the-dataset.png)

>[!NOTE]
>
>**Preview dataset **displays the most recent successful batch in this dataset. You will not be be able to see the previous batches. Also, complex data such as arrays and maps are not viewable today and will appear as empty columns. Do not panic! To get a more comprehensive view, you will need to use SQL to explore the dataset as explained below.



## Query Dataset

1. **Close** the Preview
1. In the Dataset screen, click the copy icon on **Table name**. In the example screen below, the table name is `customer_account_sm`

![LxxLyKc0x1oi Hyifs3cMQ76cz5HM EUrq 20241025 011617.png "Copy the table name"](assets/n-ADAXZy_lxxLyKc0x1oi-Hyifs3cMQ76cz5HM-EUrq-20241025-011617.png "Copy the table name")



3\. Navigate to **Queries **section 

4\. Click on **Create query**

![Access the query editor](assets/B92Vj2-3kGpBP37IoXmE0_access-the-query-editor.png)



5\. Copy paste the following SQL query in the** Editor**. Remember to replace `<table_name>` with the value you obtained in step 6.

```sql
SELECT * FROM <table_name>
```



6\. Press the** Play **button. 

![LxxLyKc0x1oi  5jgN 14oDYtoLIu1Ot4m 20241025 012023.png "Query editor interface"](assets/n-ADAXZy_lxxLyKc0x1oi-_5jgN_14oDYtoLIu1Ot4m-20241025-012023.png "Query editor interface")



7\. **Preview **the results

8\. Also, execute the following SQL query to retrieve the XDM schema along with the data:

```sql
SELECT to_json(shippingAddress) FROM <table_name>
```

To access the data in the `postalCode`** node**`,` you can type:

```sql
SELECT shippingAddress.postalCode FROM <table_name>
```

>[!TIP]
>
>Congratulations!  You have successfully ingested and created a sample set of Real-Time Customer Profiles


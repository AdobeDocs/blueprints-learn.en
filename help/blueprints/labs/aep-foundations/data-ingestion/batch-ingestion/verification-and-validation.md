---
hold: true
title: Verification and validation
description: Preview an ingested dataset in the UI and run SQL queries to verify batch-ingested records and nested schema fields.
doc-type: article
solution: Experience Platform
exl-id: 7e7cd43d-cc24-4a40-a175-2c651436ab79
---

# Verification and validation

## Preview the dataset

1. Click on **Datasets**
1. **Locate** and **click** the dataset name that you created.

![Locating and clicking the dataset name in the Datasets pane](assets/verification-and-validation-access-dataset-in-datasets-pane.png "Access the dataset in the Datasets pane")



1. Click on **Preview dataset** in the top right corner

![Preview dataset button location in the top right corner of the dataset screen](assets/verification-and-validation-preview-dataset-button-location.png "Preview dataset is in the top right corner")



1. **Verify** and **validate** the same records that you ingested by clicking on the left pane showing the schema hierarchy.

![Dataset preview with schema hierarchy pane showing ingested records](assets/verification-and-validation-verify-and-validate-the-dataset.png)

>[!NOTE]
>
>**Preview dataset** displays the most recent successful batch in this dataset. You are not able to see the previous batches. Also, complex data such as arrays and maps are not viewable today and appear as empty columns. Do not panic! To get a more comprehensive view, you need to use SQL to explore the dataset as explained below.



## Query dataset

1. **Close** the Preview
1. In the Dataset screen, click the copy icon on **Table name**. In the example screen below, the table name is `customer_account_sm`

![Copy icon next to the table name in the Dataset screen](assets/verification-and-validation-copy-table-name.png "Copy the table name")



1. Navigate to **Queries** section 

1. Click on **Create query**

![Create query button in the Queries section](assets/verification-and-validation-access-the-query-editor.png)



1. Copy paste the following SQL query in the **Editor**. Remember to replace `<table_name>` with the value you obtained in step 6.

```sql
SELECT * FROM <table_name>
```



1. Press the **Play** button. 

![Query editor interface with SQL query and Play button](assets/verification-and-validation-query-editor-interface.png "Query editor interface")



1. **Preview** the results

1. Also, execute the following SQL query to retrieve the XDM schema along with the data:

```sql
SELECT to_json(shippingAddress) FROM <table_name>
```

To access the data in the `postalCode` **node**, you can type:

```sql
SELECT shippingAddress.postalCode FROM <table_name>
```

>[!TIP]
>
>Congratulations!  You have successfully ingested and created a sample set of Real-Time Customer Profiles

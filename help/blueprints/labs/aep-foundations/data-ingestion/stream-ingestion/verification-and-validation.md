---
title: Verification and validation
description: Preview a streamed dataset in the UI and run SQL queries to verify ingested records and nested schema fields.
doc-type: article
solution: Experience Platform
exl-id: fbdb0b6b-08b6-49b8-b6ab-d59d5941c678
---

# Verification and validation

## Preview the dataset

1. Click on **Datasets**
1. **Locate** and **click** the dataset name that you created.

![Accessing the created dataset in the Datasets pane](assets/verification-and-validation-access-the-dataset-in-the-datasets-pane.png "Access the dataset in the Datasets pane")



1. Click on **Preview dataset** in the top right corner

![Preview dataset button located in the top right corner of the dataset screen](assets/verification-and-validation-preview-dataset-button.png "Preview dataset is in the top right corner ")



1. **Verify** and **validate** the same records that you ingested by clicking on the left pane showing the schema hierarchy.

![Verifying and validating ingested records using the schema hierarchy pane](assets/verification-and-validation-verify-and-validate-the-dataset.png "Verify and validate the dataset")

>[!NOTE]
>
>**Preview dataset** will only show the first few rows of the dataset. Array objects are not viewable. 



## Query dataset

1. **Close** the Preview
1. In the Dataset screen, click the copy icon on **Table name**. In the example screen below, the table name is `customer_account_sm`

![Copying the table name from the Dataset screen for use in a query](assets/verification-and-validation-copy-the-table-name.png "Copy the table name")



1. Navigate to **Queries** section 

1. Click on **Create query**

![Accessing the query editor from the Queries section](assets/verification-and-validation-access-the-query-editor.png "Access the query editor")



1. Turn the toggle for **Enhanced Query Editor**

![Query editor interface with the Enhanced Query Editor toggle enabled](assets/verification-and-validation-enhanced-query-editor-toggle.png "Query editor interface")



1. Copy paste the following SQL query in the **Editor**. Remember to replace `<table_name>` with the value you obtained in step 2.

```sql
SELECT * FROM <table_name>
```



1. Press the **Play** button. 

1. **Preview** the results. 

1. Also, execute the following SQL query to retrieve the XDM schema along with the data:

```sql
SELECT to_json(shippingAddress) FROM <table_name>
```



1. To access the data in the `postalCode` **node**, you can type:

```sql
SELECT shippingAddress.postalCode FROM <table_name>
```

>[!TIP]
>
>Congratulations!  You have successfully ingested and created a sample set of Real-Time Customer Profiles

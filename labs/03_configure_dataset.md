# 3. Map Dataset to Target Data Store

| Persona | Time  |
| -----  | ----- |
| Data Consumer | 5 minutes |

## Summary
In this lab, you will:
* Open an Azure Data Share invitation
* Review the terms of use
* Map the share to a target data share account
* Create a share subscription

![alt text](../images/azure_data_share_data_consumer.png "Azure Data Share - Data Consumer")

## Steps

1. Navigate to your Azure Data Share resource
2. Click **Received Shares**
3. Click **Datasets**
![alt text](../images/azure_data_share_configure_dataset.png "Azure Data Share - Configure Dataset")

The next screen will show a list of datasets within the share with the following attributes:
*  Dataset Name
* Source Type (e.g. Azure Blob Storage Container)
* Source Path (e.g. sales)
* Status (e.g. Not Mapped)
* Target Type

4. Select the dataset (e.g. dataset_contoso_sales) by clicking the checkbox
5. Click **Map to target**
![alt text](../images/azure_data_share_map_target.png "Azure Data Share - Configure Dataset")

6. Map the dataset to target datastore by making the following selections:
    * Target data type (e.g. Azure Blob Storage)
    * Subscription
    * Resource group
    * Storage account
    * Container name (e.g. landing-zone)
7. Click **Map to target**
![alt text](../images/azure_data_share_configure_target.png "Azure Data Share - Map to Target")

At this point, you will return to the **Received Shares** screen and see a notification that the dataset was mapped successfully.
![alt text](../images/azure_data_share_received_share_mapped.png "Azure Data Share - Mapped Dataset")

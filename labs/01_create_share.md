## 1. Create a Sent Share
1. Navigate to your Azure Data Share resource
2. Click **Sent Shares**
3. Click **Create**
![alt text](../images/azure_data_share_sent_share_create.png "Azure Data Share - Create Sent Share")

4. Populate the following fields:
    * Share Name (e.g. share_contoso_sales)
    * Share Type (Snapshot)
    * Description
    * Terms of use

5. Click **Continue**
![alt text](../images/azure_data_share_sent_share_details.png "Azure Data Share - Share Details")

6. Click **Add datasets**
![alt text](../images/azure_data_share_sent_share_add_dataset.png "Azure Data Share - Add Datasets")

7. Select **Azure Blob Storage**
8. Click **Next**
![alt text](../images/azure_data_share_sent_share_dataset_type.png "Azure Data Share - Dataset Type")

9. Under **Subscriptions** select your Azure subscription
10. Under **Resource groups** select the resource group that contains the Azure Blob Storage account
11. Expand the storage hierarchy and select the **sales** container
12. Click **Next**
![alt text](../images/azure_data_share_sent_share_blob_storage.png "Azure Data Share - Azure Blob Storage (Configure)")

13. Provide a **Dataset Name** (e.g. dataset_contoso_sales)
14. Click **Add datasets**
![alt text](../images/azure_data_share_sent_share_add_storage.png "Azure Data Share - Azure Blob Storage (Dataset Name)")

15. Click **Continue**
![alt text](../images/azure_data_share_sent_share_datasets.png "Azure Data Share - Datasets")

16. Click **Add recipient**
17. Enter the recipients Azure login email address
18. Click **Continue**
![alt text](../images/azure_data_share_sent_share_recipient.png "Azure Data Share - Recipients")

19. Click the checkbox to enable **Snapshot schedule**
20. Choose a desired **Start time** by configuring the date and time fields
21. Select a **Recurrence** (e.g. Daily)
22. Click **Continue**
![alt text](../images/azure_data_share_sent_share_snapshot.png "Azure Data Share - Snapshot Settings")

23. Review the details of your share and click **Create**
- Number of datasets
- Name of data share
- Description
- Terms of use
- Number of recipients
- Snapshot settings
![alt text](../images/azure_data_share_sent_share_review.png "Azure Data Share - Review and Create")

At this point, you will return to the **Sent Shares** screen and see several notifications indicating that your share has been created successfully.
* New data share was created successfully
* Invitations were added successfully
* Datasets were added successfully
![alt text](../images/azure_data_share_sent_share_success.png "Azure Data Share - Notifications")

Note: As part of the data share creation process, the Azure Data Share resource is granted the appropriate level of access to read data from the source data store, in this case - Storage Blob Data Reader. This can be verified by navigating to the Azure Storage Account > Access Control (IAM) and clicking **Role assignments**.
![alt text](../images/azure_data_share_sent_share_role_assignment.png "Azure Data Share - Storage Blob Data Reader")
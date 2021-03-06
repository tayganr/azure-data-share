# Azure Data Share
Azure Data Share is a fully managed service that enables organisations to share data across tenants (B2B), simply and securely. Data can be consumed as needed by triggering a full copy or incremental update. Alternatively, data can be received automatically at a regular interval, as defined by the data provider.

![alt text](images/azure_data_share_concept.png "Azure Data Share")

## Lab Solution Template
This template encompasses two Azure resources:
1. Azure Storage Account
2. Azure Data Share Account

You can click the "Deploy to Azure" button to deploy the solution directly from GitHub. Note: The solution template will only deploy one set of resources, representing one of the two personas used in this lab (data consumer and data provider). A second set of resources will need to be deployed to mimic both personas, whether that be in the same Azure subscription, or in a completely distinct tenant. In which case, you can click the "Deploy to Azure" button a second time so that before you start the lab modules, there are two sets of resources - one for the data consumer, and the other for the data provider.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ftayganr%2Fazure-data-share%2Fmaster%2Fazuredeploy.json)  

## Post Resource Deployment (PowerShell)
The PowerShell script below will do the following:  

**Data Provider**
1. Create a `sales` container within your storage account.
2. Generate two dummy CSV files (sales01.csv, sales02.csv).
3. Upload CSV files to your storage account within the `sales` container.

**Data Consumer**
1. Create a `landing-zone` container within your storage account.

Note: You will need to update the name of the variable `$rg` with the name of your resource group.

### Data Provider
```powershell
# Define Variables
$rg = 'share_provider'
$storage = az storage account list --resource-group $rg --output json --query "[0].name"
$container = 'sales'
$csv1_filename = 'sales01.csv'
$csv2_filename = 'sales02.csv'

# Dummy Data
$csv1_data = @'
"business_unit","amount"
"marketing",233
"finance",318
"sales",322
'@
$csv2_data = @'
"business_unit","amount"
"marketing",675
"finance",54
"sales",224
'@

# 1. Create a container within the storage account
az storage container create --name $container --resource-group $rg --account-name $storage --output table

# 2. Generate CSV files
$csv1_data >> $csv1_filename
$csv2_data >> $csv2_filename

# 3. Upload CSV files to storage
az storage blob upload --account-name $storage --container-name $container --name $csv1_filename --file $csv1_filename --output table
az storage blob upload --account-name $storage --container-name $container --name $csv2_filename --file $csv2_filename --output table

# 4. Clean-up CSV files
rm $csv1_filename
rm $csv2_filename
```

### Data Consumer
```powershell
# Define Variables
$rg = 'share_consumer'
$storage = az storage account list --resource-group $rg --output json --query "[0].name"
$container = 'landing-zone'

# Create a container within the storage account
az storage container create --name $container --resource-group $rg --account-name $storage --output table
```

## Lab Prerequisites

**Data Provider**
These prerequisites can be met by clicking "Deploy to Azure" button above and running the Data Provider post resource deployment script.
1. [Azure Subscription](https://azure.microsoft.com/en-us/free/)
2. [Create an Azure Resource Group](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal#create-resource-groups) (e.g. datashare_rg_provider)
3. [Create an Azure Storage Account](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-create?tabs=azure-portal) (e.g. datastorageprovider<random_id>)
4. Create a container within your Storage Account (e.g. sales)
5. Upload some dummy data files within the container (e.g. sales001.csv, sales002.csv, etc.)
4. [Create an Azure Data Share Account](https://docs.microsoft.com/en-us/azure/data-share/share-your-data#create-a-data-share-account) (e.g. datashare_acct_provider)

**Data Consumer**
These prerequisites can be met by clicking "Deploy to Azure" button above and running the Data Consumer post resource deployment script.
1. [Azure Subscription](https://azure.microsoft.com/en-us/free/)
2. [Create an Azure Resource Group](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal#create-resource-groups) (e.g. datashare_rg_consumer)
3. [Create an Azure Storage Account](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-create?tabs=azure-portal) (e.g. datastorageconsumer<random_id>)
4. Create a container within your Storage Account (e.g. landing-zone)
5. [Create an Azure Data Share Account](https://docs.microsoft.com/en-us/azure/data-share/share-your-data#create-a-data-share-account) (e.g. datashare_acct_consumer)

Disclaimer:
* For the purposes of the demo, the set of Azure resources for both the data provider (Contoso) and the data consumer (Wingtip Toys) will belong to the same Azure subscription under the same tenant.
* In reality, a more likely scenario will involve the data provider and data consumer belonging to completely distinct organizations (i.e. B2B) with their own Azure subscriptions under seperate tenants.
* That said, the process of creating a data share, having an invitation sent out, the invitation being accepted, and ultimately the data consumer mapping the shared data into their environment is the same.

## Lab Modules
* Lab 1 - [Create a Sent Share](/labs/01_create_share.md)
* Lab 2 - [Accept an Azure Data Share Invitation](/labs/02_accept_invitation.md)
* Lab 3 - [Map Dataset to Target Data Store](/labs/03_configure_dataset.md)
* Lab 4 - [Configure a Snapshot Schedule](/labs/04_configure_snapshot.md)
* Lab 5 - [Trigger a Snapshot](/labs/05_trigger_snapshot.md)
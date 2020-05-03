# 2. Accept an Azure Data Share Invitation

## Table of Contents
[Azure Data Share Lab](../README.md)
* Lab 1 - [Create a Sent Share](../labs/01_create_share.md)
* Lab 2 - Accept an Azure Data Share Invitation
* Lab 3 - [Map Dataset to Target Data Store](../labs/03_configure_dataset.md)
* Lab 4 - [Configure a Snapshot Schedule](../labs/04_configure_snapshot.md)
* Lab 5 - [Trigger a Snapshot](../labs/05_trigger_snapshot.md)

## Overview
| Persona | Time | Action |
| -----  | ----- | ----- |
| Data Consumer | 5 minutes | Accept invitation |

## Summary
In this lab, you will:
* Open an Azure Data Share invitation
* Review the terms of use
* Map the share to a target data share account
* Create a share subscription

![alt text](../images/azure_data_share_data_consumer.png "Azure Data Share - Data Consumer")

## Steps

1. Open your email client to review the invitation
2. Click **View invitation**
![alt text](../images/azure_data_share_invitation.png "Azure Data Share - Invitation Email")

Once logged in, you will see a list of **Data Share Invitations** with the following attributes:
* Invitation
* Sender
* Company
* Status (e.g. Pending)
* Received On (Date Time)  
3. Click **`[invitation_name]`**
![alt text](../images/azure_data_share_pending_invitations.png "Azure Data Share - Invitation Email")

Review the details of the invitation:
* From (Full Name)
* Company
* Number of datasets
* Description
* Terms of use

4. Click **I agree to terms of use**
5. Map the **Target Data Share Account**
   * Subscription
   * Resource group
   * Data share account
   * Received share name
6. Click **Accept and configure**
![alt text](../images/azure_data_share_target_account.png "Azure Data Share - Target Data Share Account")

At this point, you will return to the **Received Shares** screen and see a notification that you have successfully created a share subscription.
![alt text](../images/azure_data_share_subscription.png "Azure Data Share - Created Subscription")
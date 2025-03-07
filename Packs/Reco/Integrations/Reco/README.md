Reco is a Saas data security solution that protects your data from accidental leaks and malicious attacks.

## Configure Reco on Cortex XSOAR

1. Navigate to **Settings** > **Integrations** > **Servers & Services**.
2. Search for Reco.
3. Click **Add instance** to create and configure a new integration instance.

    | **Parameter** | **Description** | **Required** |
    | --- | --- | --- |
    | Server URL (e.g. https://host.reco.ai/api/v1) |  | True |
    | JWT app token |  | True |
    | Trust any certificate (not secure) |  | False |
    | Use system proxy settings |  | False |
    | Incident type |  | False |
    | Fetch incidents |  | False |
    | Max fetch |  | False |
    | Source | Incidents SaaS Source | False |
    | Before | Created At time before which incidents will be fetched | False |
    | After | Created At time after which incidents will be fetched | False |
    | Risk level | Risk level of the incidents to fetch | False |
    | First fetch timestamp (&lt;number&gt; &lt;time unit&gt;, e.g., 12 hours, 7 days) |  | False |

4. Click **Test** to validate the URLs, token, and connection.

## Commands

You can execute these commands from the Cortex XSOAR CLI, as part of an automation, or in a playbook.
After you successfully execute a command, a DBot message appears in the War Room with the command details.

### reco-update-incident-timeline

***
Add a comment to an incident in Reco

#### Base Command

`reco-update-incident-timeline`

#### Input

| **Argument Name** | **Description** | **Required** |
| --- | --- | --- |
| comment | Comment to add to the incident. | Required | 
| incident_id | Incident ID to add the comment to. | Required | 

#### Context Output

There is no context output for this command.
### reco-resolve-visibility-event

***
Resolve an event in Reco Finding. Reco Findings contains aggregations of events. This command resolves the event in the Reco Finding.

#### Base Command

`reco-resolve-visibility-event`

#### Input

| **Argument Name** | **Description** | **Required** |
| --- | --- | --- |
| entity_id | entity id of the file to resolve. | Required | 
| label_name | label name to resolve (e.g. "Accessible to All Org Users", "Accessible by General Public"). | Required | 

#### Context Output

There is no context output for this command.
### reco-get-risky-users

***
Get Risky Users from Reco

#### Base Command

`reco-get-risky-users`

#### Input

| **Argument Name** | **Description** | **Required** |
| --- | --- | --- |

#### Context Output

| **Path** | **Type** | **Description** |
| --- | --- | --- |
| Reco.RiskyUsers | unknown | Risky Users | 

### reco-add-risky-user-label

***
Tag a user as risky in Reco

#### Base Command

`reco-add-risky-user-label`

#### Input

| **Argument Name** | **Description** | **Required** |
| --- | --- | --- |
| email_address | Email address of the user to add to the risky users list in Reco. | Required | 

#### Context Output

There is no context output for this command.


### reco-get-assets-user-has-access-to

***
Get assets user has access to (optional to get only sensitive assets)

#### Base Command

`reco-get-assets-user-has-access-to`

#### Input

| **Argument Name** | **Description**                                   | **Required** |
|-------------------|---------------------------------------------------|--------------|
| asset_owner       | Email address of the user who owns all the assets | Required     | 
| only_sensitive    | Get only sensitive files                          | Optional     |


#### Context Output

| **Path**    | **Type** | **Description** |
|-------------|----------|----------------|
| Reco.Assets | string   | Assets         | 



### reco-get-sensitive-assets-by-name

***
Get sensitive assets by name (optional to search by regex)

#### Base Command

`reco-get-sensitive-assets-by-name`

#### Input

| **Argument Name** | **Description**                               | **Required** |
|-------------------|-----------------------------------------------|--------------|
| asset_name        | Asset Name to search                          | Required     | 
| regex_search      | Search assets by regex (Default string equal) | Optional     |


#### Context Output

There is no context output for this command.


### reco-get-sensitive-assets-by-id

***
Get sensitive assets by id

#### Base Command

`reco-get-sensitive-assets-by-id`

#### Input

| **Argument Name** | **Description**    | **Required** |
|-------------------|--------------------|--------------|
| asset_id          | Asset ID to search | Required     |


#### Context Output


| **Path**    | **Type** | **Description** |
|-------------|----------|----------------|
| Reco.SensitiveAssets.file_name | string   |  The name of the asset |
| Reco.SensitiveAssets.file_owner | string   | The owner of the asset |
| Reco.SensitiveAssets.file_url | Unknown     |  Json string of the asset's url and the name |
| Reco.SensitiveAssets.currently_permitted_users | String   | List of currently permitted users |
| Reco.SensitiveAssets.visibility | string   |  Visibility of the asset |
| Reco.SensitiveAssets.location | string   |  The path of the asset |
| Reco.SensitiveAssets.source | string   |  SaaS tool source of the asset |
| Reco.SensitiveAssets.sensitivity_level | Number  | The sensitivity level of the asset |



### reco-add-leaving-org-user-label

***
Tag a user as leaving employee in Reco

#### Base Command

`reco-add-leaving-org-user-label`

#### Input

| **Argument Name** | **Description**                                                         | **Required** |
| --- |-------------------------------------------------------------------------| --- |
| email_address | Email address of the user to add to the leaving org users list in Reco. | Required | 

#### Context Output

There is no context output for this command.


### reco-get-link-to-user-overview-page

***
Get link to user overview page in Reco

#### Base Command

`reco-get-link-to-user-overview-page`

#### Input

| **Argument Name** | **Description**                                                             | **Required** |
|-------------------|-----------------------------------------------------------------------------| --- |
| entity_id         | Email address of the user to get the link to the user overview page in Reco. | Required |
| link_type         | Type of the link                                                            | Required |


### reco-get-sensitive-assets-with-public-link

***
Get all sensitive assets with public link from Reco

#### Base Command

`reco-get-sensitive-assets-with-public-link`

#### Input

There are no input arguments for this command.

#### Context Output

| **Path** | **Type** | **Description** |
| --- | --- | --- |
| Reco.Assets.asset_id | String | The asset id | 
| Reco.Assets.asset | Unknown | Json string of the asset's url and the name | 
| Reco.Assets.data_category | String | The data category of the asset | 
| Reco.Assets.data_categories | String | The data categories of the asset | 
| Reco.SensitiveAssets.location | String | The path of the asset | 
| Reco.SensitiveAssets.source | String | SaaS tool source of the asset | 
| Reco.Assets.last_access_date | String | The last access date of the asset | 
### reco-get-3rd-parties-accessible-to-data-list

***
Get 3rd parties accessible to sensitive assets

#### Base Command

`reco-get-3rd-parties-accessible-to-data-list`

#### Input

| **Argument Name** | **Description** | **Required** |
| --- | --- | --- |
| last_interaction_time_in_days | Last interaction time in days. | Required | 

#### Context Output

| **Path** | **Type** | **Description** |
| --- | --- | --- |
| Reco.Domains.domain | String | The domain of the 3rd party | 
| Reco.Domains.last_activity | String | The last interaction time with the 3rd party | 
| Reco.Domains.num_files | Number | The number of files the 3rd party has access to | 
| Reco.Domains.num_users | Number | The number of users the 3rd party has access to | 
| Reco.Domains.data_category | String | The data category of the assets the 3rd party has access to | 
### reco-get-files-shared-with-3rd-parties

***
Get files shared with 3rd parties

#### Base Command

`reco-get-files-shared-with-3rd-parties`

#### Input

| **Argument Name** | **Description** | **Required** |
| --- | --- | --- |
| last_interaction_time_in_days | Last interaction time in days. | Required | 
| domain | Domain to search. | Required | 

#### Context Output

| **Path** | **Type** | **Description** |
| --- | --- | --- |
| Reco.Assets.asset_id | String | The asset id of the file | 
| Reco.Assets.location | String | The location of the file | 
| Reco.Assets.users | String | Users the file is shared with | 
| Reco.Assets.asset | Unknown | The asset metadata | 
| Reco.Assets.data_category | String | The data category of the assets the 3rd party has access to | 
| Reco.Assets.last_access_date | String | The last access date of the asset | 
| Reco.Assets.domain | String | The domain of the 3rd party | 

# MDEASM: Inventory Rules/Query based Asset Management

## Overview
Logic App Template demonstrates automation that can be scheduled to run at regular intervals to update Inventory Assets by querying for certain criteria using the "filter" parameter from your MDEASM Inventory.

### Asset update options for this template are,
    1. Apply labels
    2. Change Asset Status
    3. Do both Change Asset Status and Apply label


1. The template queries MDEASM Inventory using the 'filter' parameter and updates inventory Asset results
2. The 'RunFrequency' parameter (In Hours) can be used to change the schedule to run the playbook as needed. By default it is run very 24 Hours.
3. The 'LabelName' parameter is used to apply the label by the playbook on the resultant Inventory Assets. The playbook will create a new label, if the label provided doesn't already exist in the EASM Workspace.
4. The 'StateValue' parameter is used to mention the New Changed State needed for Inventory Assets. allowed Asset state values: archived, candidate, associatedThirdparty, associated, dismissed, candidateInvestigate, confirmed, associatedPartner.
5. The template also checks the status of the EASM Update till it completes successfully within the EASM Workspace.
6. The template will remain in running state or fail if the update takes more than 2 hours to complete.

## Prerequisites
1. MDEASM API in this template supports managed identity Authentication which requires you to have a user-assigned managed identity setup with the appropriate permissions and used for authorization.
2. Atleast one of the parameters 'LabelName' and/or 'StateValue' is needed to be set for the template to run.
3. MDEASM filter parameter needs to be set to an appropriate value to query inventory assets. Refer MDEASM API documentation For Example: here's a query to monitor and alert for all assets with CVSS Score >= 8 state="confirmed" and kind = "page" and rooturl = true and cvssScore >= 8

## Deployment

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Frandallhuff%2FEASI%2Frefs%2Fheads%2Fmain%2FAutomation%2FInventory-Asset-Management%2FEASI-MI-Template.json)

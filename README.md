# Mark-rg

## Instructions on deploying the mark-rg template to azure.

Requirements:
    An Azure account, with activated subscription.
    Powershell core installed 
    Powershell plugin AzureRM installed
    
This ARM template mark-rg.json can be deployed natively within zure, or via powershell as follows.



1.  Ensure that you have version >=7.1 of Powershell Core installed:  https://github.com/PowerShell/PowerShell#get-powershell


2.  Install the Azure plugin for Powershell by executing the following within powershell:

if ($PSVersionTable.PSEdition -eq 'Desktop' -and (Get-Module -Name AzureRM -ListAvailable)) {
    Write-Warning -Message ('Az module not installed. Having both the AzureRM and ' +
      'Az modules installed at the same time is not supported.')
} else {
    Install-Module -Name Az -AllowClobber -Force
}


3.   Connect to Azure with a browser sign in token by executing the following within powershell:
   
Connect-AzAccount


3.  Create The resource group in Azure.   The Resource group is the "Container" which contains associated resources.  In powershell, execute:

New-AzResourceGroup -Name mark-rg -Location westus2


4.  Deploy the template to create the resources in the RG:

New-AzResourceGroupDeployment -ResourceGroupName mark-rg -TemplateUri https://raw.githubusercontent.com/dswan2/Mark-rg/main/mark-rg.json





[![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https://raw.githubusercontent.com/dswan2/Mark-rg/main/mark-rg.json)


[![Visualize](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/visualizebutton.svg?sanitize=true)](http://armviz.io/#/?load=https://raw.githubusercontent.com/dswan2/Mark-rg/main/mark-rg.json)

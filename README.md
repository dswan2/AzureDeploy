# daniel-rg

## Instructions on deploying the daniel-rg template to azure.

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

New-AzResourceGroup -Name daniel-rg -Location westus2


4.  Deploy the template to create the resources in the RG:

New-AzResourceGroupDeployment -ResourceGroupName mark-rg -TemplateUri https://raw.githubusercontent.com/dswan2/daniel-rg/main/daniel-rg.json




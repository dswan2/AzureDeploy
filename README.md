# Azuredeploy - Create an Azure environment from template.

## Instructions on deploying the daniel-rg template to azure.

Requirements:  
    - An Azure account, with activated subscription.   
    - Powershell core installed  
    - Powershell plugin AzureRM installed  
    
This ARM template daniel-rg.json can be deployed natively within Azure, or via powershell as follows.



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


3.  Set your Source IP to allow whitelist:

$additionalParams = @{ "Whitelist_IP" = "1.2.3.3" }


4.  Deploy the template to create the resources in the RG (idempotent):

New-AzResourceGroupDeployment -ResourceGroupName daniel-rg -TemplateUri https://raw.githubusercontent.com/dswan2/AzureDeploy/main/daniel-rg.json  -TemplateParameterObject $additionalParams


Optional:  To delete resource group and clean the slate for redeploy, In powershell, execute:

Remove-AzResourceGroup -Name daniel-rg -Force  



# Todos:
  
Breakout Allowed-IP into command line parameter?  
Manually add customdata to template  


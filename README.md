# Mark-rg

## Instructions on deploying this template to azure.

1.  Ensure the Azure powershell plugin is installed by executing the following in a Powershell session.   Administrator access not required.

if ($PSVersionTable.PSEdition -eq 'Desktop' -and (Get-Module -Name AzureRM -ListAvailable)) {
    Write-Warning -Message ('Az module not installed. Having both the AzureRM and ' +
      'Az modules installed at the same time is not supported.')
} else {
    Install-Module -Name Az -AllowClobber -Scope CurrentUser
}


2.  Create The resource group in Azure.   The Resource group is the "Container" which contains associated resources.  In powershell, execute:

New-AzResourceGroup -Name mark-rg -Location westus2






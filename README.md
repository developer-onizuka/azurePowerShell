# azurePowerShell


# 1. Pull Ubuntu and run
```
$ docker run --rm -it --name ubuntu ubuntu:18.04 /bin/bash
```

# 2. Install PowerShell
https://docs.microsoft.com/en-us/learn/modules/automate-azure-tasks-with-powershell/4-exercise-install-azure-powershell?pivots=linux
```
# apt-get update
# apt-get install -y curl sudo
# apt-get install -y gnupg gnupg2 gnupg1
# curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
# sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list
# sudo apt-get update
# sudo apt-get install -y powershell
```

# 3. Run PowerShell
```
# pwsh
PowerShell 7.2.1
Copyright (c) Microsoft Corporation.

https://aka.ms/powershell
Type 'help' to get help.

PS /root> 
```

# 4. Install Azure module for the PowerShell
https://docs.microsoft.com/en-us/learn/modules/automate-azure-tasks-with-powershell/5-create-resource-interactively?pivots=linux
```
PS /root> Install-Module -Name Az -Scope CurrentUser -Repository PSGallery -Force
```

# 5. Connect the PowerShell to the Azure Subscription thru Azure AD account
```
PS /root> Connect-AzAccount -UseDeviceAuthentication
PS /root> Get-AzContext                               

Name                                     Account                    SubscriptionName           Environment                TenantId
----                                     -------                    ----------------           -----------                --------
xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx  -… xxxxxxx…                   Concierge Subscription     AzureCloud                 xxxxxxxx-xxxx-xxxx-xxxx-…
```
```
PS /root> New-AzResourceGroup -Name <name> -Location <location>
```

# 5. User PowerShell Script to create VM
https://docs.microsoft.com/en-us/learn/modules/automate-azure-tasks-with-powershell/8-exercise-create-resource-using-script

```
cat << EOF > ConferenceDailyReset.ps1 
param([string]\$resourceGroup)
\$adminCredential = Get-Credential -Message "Enter a username and password for the VM administrator."
For (\$i = 1; \$i -le 3; \$i++)
{
    \$vmName = "ConferenceDemo" + \$i
    Write-Host "Creating VM: " \$vmName
    New-AzVm -ResourceGroupName \$resourceGroup -Name \$vmName -Credential \$adminCredential -Image UbuntuLTS
}
EOF
```
```
PS /root> ./ConferenceDailyReset.ps1 xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

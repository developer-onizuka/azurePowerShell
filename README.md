# azurePowerShell


```
$ docker run --rm -it --name ubuntu ubuntu:18.04 /bin/bash
```

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
```
# pwsh
PowerShell 7.2.1
Copyright (c) Microsoft Corporation.

https://aka.ms/powershell
Type 'help' to get help.

PS /root> 
```

https://docs.microsoft.com/en-us/learn/modules/automate-azure-tasks-with-powershell/5-create-resource-interactively?pivots=linux

```
PS /root> Install-Module -Name Az -Scope CurrentUser -Repository PSGallery -Force
```
```
PS /root> Connect-AzAccount -UseDeviceAuthentication
PS /root> Get-AzContext                               

Name                                     Account                    SubscriptionName           Environment                TenantId
----                                     -------                    ----------------           -----------                --------
xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx  -… xxxxxxx…                   AzureCloud                                            xxxxxxxx-xxxx-xxxx-xxxx-…
```

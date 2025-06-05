#### **Install DBeaver**
**MAC**
```bash
brew install --cask dbeaver-community

#launch
open -a "DBeaver"
```
**Ubuntu**
```bash
wget https://dbeaver.io/files/dbeaver-ce_latest_amd64.deb
sudo apt update
sudo apt install ./dbeaver-ce_latest_amd64.deb
sudo apt --fix-broken install

#launch
dbeaver &
```
**Windows**
```PowerShell
#using winget
winget install --id DBeaver.DBeaverCE -e

#using chocolatey
#install chocolatey first
Set-ExecutionPolicy Bypass -Scope Process -Force; `
[System.Net.ServicePointManager]::SecurityProtocol = `
[System.Net.ServicePointManager]::SecurityProtocol -bor 3072; `
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

choco --version

choco install dbeaver

#launch using Start menu or commandline
dbeaver
```

#### **Connecting to Azure MySQL Server using dbeaver**
![https://github.com/devopsmatic/mysql-demo/blob/main/Hosting%20Websites.png?raw=true)

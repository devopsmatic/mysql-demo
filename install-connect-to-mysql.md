**Create a minimal MySQL database in Azure using CLI** (`az`), targeting **Azure Database for MySQL - Flexible Server** (recommended by Microsoft).
#### 1. **Set variables**
```bash
# Customize these values
RESOURCE_GROUP="my-rg"
LOCATION="eastus2"
MYSQL_NAME="myflexmysqlserver123"   # must be globally unique
ADMIN_USER="mysqladmin"
ADMIN_PASS="YourStrongP@ssw0rd"
```
#### 2. **Create Resource Group**
```bash
az group create --name $RESOURCE_GROUP --location $LOCATION
```
#### 3. **Create MySQL Flexible Server (Basic Tier)**
```bash
az mysql flexible-server create \
  --name $MYSQL_NAME \
  --resource-group $RESOURCE_GROUP \
  --location $LOCATION \
  --admin-user $ADMIN_USER \
  --admin-password $ADMIN_PASS \
  --sku-name Standard_B1ms \
  --storage-size 20 \
  --tier Burstable \
  --version 8.0 \
  --public-access 0.0.0.0-255.255.255.255   # or set specific IP
```
🔹 This creates the **minimum configuration** (Basic tier, 1 vCore, 20 GB storage).

#### 4. **Create a Database**
```bash
az mysql flexible-server db create \
  --resource-group $RESOURCE_GROUP \
  --server-name $MYSQL_NAME \
  --database-name mydb
  ```
  5. **Test Connection (Optional)**
**Windows:** Download MySQL Installer
https://dev.mysql.com/downloads/installer/

**Ubuntu:**
```bash
sudo apt update
sudo apt install mysql-client
```
MacOS
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

brew install mysql-client

echo 'export PATH="/usr/local/opt/mysql-client/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc [If you are nusing zsh]
OR
echo 'export PATH="/usr/local/opt/mysql-client/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc [If you are nusing bash]

mysql --version
```
Connecting remotely to Azure MYSQL Server
  ```bash
  mysql -h $MYSQL_NAME.mysql.database.azure.com -u $ADMIN_USER@$MYSQL_NAME -p
```

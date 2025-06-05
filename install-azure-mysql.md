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
 


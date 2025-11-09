## ⚙️ Steps to Set Up Alembic

### 🔧 1. Install Required Packages

You can install Alembic and SQLAlchemy directly using:
```bash
pip install alembic sqlalchemy
```

### If you’re using Microsoft SQL Server (MSSQL), install the ODBC driver as well:
```bash
pip install pyodbc
```

### 💡 Note: All the required packages with specific versions are listed in the requirements.txt file.

To install them all at once, simply run:
```bash
pip install -r requirements.txt
```

### 🏗️ 2. Initialize Alembic

Run this command inside your project root to create the Alembic directory:
```bash
alembic init alembic
```
This will generate:

- alembic.ini → Configuration file

- alembic/ → Folder containing migration environment and scripts

### ⚙️ 3. Configure Database URL

Open the alembic.ini file and update the database URL inside:
```ini
sqlalchemy.url = mssql+pyodbc://<username>:<password>@<server>/<database>?driver=ODBC+Driver+17+for+SQL+Server
```

Alternatively, use an environment variable in your .env file:
```ini
DATABASE_URL=mssql+pyodbc://sa:ABC@123@LAPTOP-ABC/AMD_DB?driver=ODBC+Driver+17+for+SQL+Server
```

### Note: when we use Alternatively DATABASE_URL from .env,have to leave alembic.ini as blank else directly can have connection string,
```ini
sqlalchemy.url = driver://user:pass@localhost/dbname
```
To
```ini
sqlalchemy.url = 
```

### 🧩 4.Modify and Configure albemic/env.py
In alembic/env.py, import your Base model metadata to support autogenerate:
```python
from app.core.database import Base
from app.model.Users import User  # Import models here
import os

# this is the Alembic Config object, which provides
# access to the values within the .ini file in use.
config = context.config

# Get database URL from .env
database_url = os.getenv("DATABASE_URL")
if not database_url:
    raise ValueError("DATABASE_URL not found in .env file")

# Set Alembic’s sqlalchemy.url dynamically
config.set_main_option("sqlalchemy.url", database_url)
```

This make sure,
- .env values are loaded securely.

- alembic.ini stays clean (avoids exposing DB credentials).

- Alembic dynamically picks the URL from .env.

- Metadata from your models (Base.metadata) ensures autogeneration works.


### 📝 5. Create a Migration

Once your models are ready, you can generate and apply migrations using Alembic.
#### ⚙️ Step 1: Generate Migration Script

Run the following command to autogenerate a new migration file based on your models:
```bash
alembic revision --autogenerate -m "create user table"
```
Execution:

![alt text](image.png)

This will create a new migration script under the versions/ folder inside your Alembic directory.

🗂 Example structure:,
![alt text](image-2.png)

#### ⚙️ Step 2: Apply Migration to Database

Apply the generated migration script to your database:

```bash
alembic upgrade head
```
![alt text](image-1.png)

#### Step 3: Verify Database

After running the upgrade command, the users table (and any other defined models) will be created in your MS SQL database — in this case, the AMD_DB.
Tables created MS SQL in THE AMD_DB

![alt text](image-3.png)


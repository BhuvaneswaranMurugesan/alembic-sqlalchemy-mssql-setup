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

# alembic-sqlalchemy-mssql-setup

🧩 Alembic + SQLAlchemy + MS SQL Setup

This repository demonstrates how to set up Alembic with SQLAlchemy for Microsoft SQL Server (MS SQL) to manage database schema migrations efficiently and securely.

📖 What is Alembic?

Alembic is a lightweight database migration tool used with SQLAlchemy.
It lets you version control your database schema — just like Git does for your code.

Whenever your models change, Alembic tracks those changes and generates migration scripts that can upgrade or downgrade your database automatically.

🔹 Why We Use Alembic

- Keeps schema in sync across development, staging, and production.

- Avoids manual SQL ALTER statements.

- Works seamlessly with SQLAlchemy models.

- Enables rollback in case of issues.

- Easy to integrate in CI/CD pipelines.

⚙️ Advantages

✅ Tracks schema changes automatically.
✅ Version control for database structure.
✅ Safe rollbacks using downgrade commands.
✅ Works with many databases (Postgres, MySQL, MS SQL, etc.)

⚠️ Disadvantages

❌ Requires careful merge handling when multiple developers create migrations at once.
❌ Must ensure models are imported correctly into Alembic’s env.py

🧠 What is SQLAlchemy?

SQLAlchemy is a powerful Python ORM (Object-Relational Mapper).
It lets you define your database tables and relationships in Python classes instead of raw SQL.

Alembic depends on SQLAlchemy to read these models and detect changes.

🔹 Role of SQLAlchemy in this Setup

- Defines tables using Python classes (Base, Column, Integer, String, etc.).

- Provides Base.metadata that Alembic uses for autogeneration.

- Creates the engine connection to MS SQL.

- Simplifies queries and database interactions.

🧰 Project Structure
alembic-sqlalchemy-mssql-setup/
```
│
├── alembic/                 # Migration scripts & env configuration
│   ├── versions/            # Auto-generated migration files
│   └── env.py               # Alembic environment setup
│
├── app/
│   ├── core/
│   │   └── database.py      # SQLAlchemy engine & Base setup
│   └── models/
│       └── user.py          # Example SQLAlchemy model
│
├── .env                     # Database URL (ignored in Git)
├── alembic.ini              # Alembic config file
├── README.md
└── requirements.txt
```
### Note : The required packages and migration commands are provided in the migration-setup-alembic folder.

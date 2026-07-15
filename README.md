# Employee Management System

A web application for managing employee records — built with ASP.NET Core MVC, Entity Framework Core, and SQL Server, with JWT-based authentication protecting access to the dashboard.

## Features

- **Authentication** — user login secured with JWT (JSON Web Tokens)
- **Employee dashboard** — view all employees in one place
- **Add employees** — create new employee records (name, department, email, designation)
- **Edit employees** — update existing employee details
- **Delete employees** — remove employee records
- **Duplicate prevention** — blocks adding an employee with an email that's already in use

## Tech Stack

- **Backend:** ASP.NET Core MVC (.NET 10)
- **Data access:** Entity Framework Core (Code-First, with migrations)
- **Database:** SQL Server
- **Auth:** JWT (JSON Web Tokens)
- **Frontend:** Razor Views

## Project Structure

```
MyFirstMVCApp/
├── Controllers/
│   ├── AuthController.cs        # Login / authentication
│   └── DashboardController.cs   # Employee CRUD operations
├── Models/
│   ├── Employee.cs              # Employee entity
│   ├── User.cs                  # Login user entity
│   └── AppDbContext.cs          # EF Core DbContext
├── Migrations/                  # EF Core migrations
├── Views/
│   ├── Auth/
│   └── Dashboard/
├── appsettings.json             # App configuration (DB connection string, JWT settings)
└── appsettings.Development.json # Local-only overrides (not committed — see below)
```

## Getting Started

### Prerequisites
- [.NET 10 SDK](https://dotnet.microsoft.com/download)
- SQL Server (Express edition works fine) — [download here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- Visual Studio 2026+ or VS Code

### Setup

1. Clone the repo
   ```bash
   git clone https://github.com/<your-username>/employee-management-system.git
   ```
2. Update the connection string in `MyFirstMVCApp/appsettings.json` to point at your local SQL Server instance:
   ```json
   "DefaultConnection": "Server=localhost\\SQLEXPRESS;Database=MyFirstMVCApp;TrustServerCertificate=True;Trusted_Connection=True;Encrypt=false;"
   ```
3. Set your own JWT signing key. `appsettings.json` ships with a placeholder — add a `MyFirstMVCApp/appsettings.Development.json` file (git-ignored, so it never gets committed) with your own key:
   ```json
   {
     "Jwt": {
       "Key": "<your own long random secret string>"
     }
   }
   ```
4. Run the app — migrations apply automatically on startup:
   ```bash
   cd MyFirstMVCApp
   dotnet restore
   dotnet run
   ```

## Notes

This project was built as a learning exercise to practice full-stack development with ASP.NET Core MVC, EF Core, and token-based authentication — covering CRUD operations, database migrations, and securing routes with JWT.

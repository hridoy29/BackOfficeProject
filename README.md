# BackOfficeProject

**BackOfficeProject** is a course-selling management system built with .NET 8. This application serves as a back-office platform to manage courses, instructors, students, and transactions, streamlining the administration of online course sales.

## Table of Contents
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Database Migrations](#database-migrations)
- [Multi-Project Solution Structure](#multi-project-solution-structure)
- [Running the Project](#running-the-project)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)

## Features
- Manage course catalog: create, update, and delete courses.
- Track student enrollments and manage student data.
- Manage instructor profiles and assigned courses.
- View and analyze sales transactions and revenue.
- Admin dashboard with insights and analytics.

## Tech Stack
- **Backend:** .NET 8, ASP.NET Core (Web API, MVC, gRPC)
- **Frontend:** Razor Pages or Blazor
- **Database:** SQL Server (or another relational database)
- **Authentication & Authorization:** JWT
- **Logging:** Serilog (optional)

## Prerequisites
- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) installed
- [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) installed (or compatible database)
- [Git](https://git-scm.com/downloads) installed
- (Optional) [Visual Studio 2022](https://visualstudio.microsoft.com/downloads/) or [Visual Studio Code](https://code.visualstudio.com/) for development

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/BackOfficeProject.git
   cd BackOfficeProject
   ```

2. **Set up the database:**
   - Open `appsettings.json` or `appsettings.Development.json` in the **startup project** (`WebApi` or `WebApp`).
   - Update the `ConnectionStrings` section with your SQL Server connection details:
     ```json
     "ConnectionStrings": {
       "DefaultConnection": "Server=your_server;Database=BackOfficeDB;User Id=your_username;Password=your_password;"
     }
     ```

## Database Migrations

### Running Migrations

1. **Add a Migration**:
   - Open a terminal in the solution’s root folder.
   - Run the following command to add a migration (replace `InitialCreate` with your migration name):
     ```bash
     dotnet ef migrations add InitialCreate --project Infrastructure --startup-project WebApi
     ```

2. **Apply the Migration**:
   - Run the following command to update the database:
     ```bash
     dotnet ef database update --project Infrastructure --startup-project WebApi
     ```

## Multi-Project Solution Structure

This solution consists of four projects:
- **Infrastructure** - Contains database models, configurations, and migrations.
- **WebApi** - Exposes RESTful APIs for the system.
- **WebApp** - An MVC application for front-end interactions.
- **WebGrpc** - Provides gRPC services.

### Project Dependencies

- Ensure `WebApi` or `WebApp` is set as the **startup project** for running the application.
- Other projects that need database access, such as `WebGrpc`, should reference `Infrastructure`.
- Migrations are managed from `Infrastructure` using `WebApi` or `WebApp` as the startup project.

## Running the Project

1. **Build the project:**
   ```bash
   dotnet build
   ```

2. **Run the project:**
   ```bash
   dotnet run --project WebApi  # Replace with WebApp if necessary
   ```

3. **Access the application:**
   - By default, the project will be hosted on `https://localhost:5001` (or the port specified in `launchSettings.json`).
   - Open a browser and navigate to `https://localhost:5001` to access the BackOffice dashboard.

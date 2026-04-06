<p align="left">
  <img src="https://img.shields.io/badge/.NET-9.0-512BD4?style=flat&logo=.net&logoColor=white" />
  <img src="https://img.shields.io/badge/C%23-13.0-239120?style=flat&logo=c-sharp&logoColor=white" />
  <img src="https://img.shields.io/badge/PostgreSQL-17-4169E1?style=flat&logo=postgresql&logoColor=white" />
  <img src="https://img.shields.io/badge/EF%20Core-ORM-512BD4?style=flat&logo=.net&logoColor=white" />
  <img src="https://img.shields.io/badge/API-PokeAPI-EF5350?style=flat" />
</p>

# Pokedex Explorer: .NET & Entity Framework Demo

<img width="782" height="590" alt="pokemon_app2" src="https://github.com/user-attachments/assets/79535247-310d-49d1-a138-f9b509dfd55f" />
<p></p>
<img width="784" height="591" alt="pokemon_app3" src="https://github.com/user-attachments/assets/438cfabf-96e0-4c7a-bbd3-e1e2fab4d0e7" />
<p></p>

**Pokedex Explorer** is a high-performance desktop application built with **WPF** and **Entity Framework Core**. It features a robust data pipeline that migrates complex astronomical-style data from **PokéAPI** into a structured **PostgreSQL** relational database, optimized for real-time filtering and search.

## Project Structure
```bash
├── pokemondb/              # Pre-configured PostgreSQL database cluster 
├── PokedexExplorer/        # Main WPF Application
│   ├── Data/               # Database Context and PokéAPI Fetcher logic
│   ├── Data/PokemonDbContext.cs 
│   ├── Models/             # Entity Framework Data Models (Pokemon, Move, etc.)
│   ├── ViewModels/         # UI Logic and Data Binding (if applicable)
│   ├── MainWindow.xaml     # Main UI Layout
│   └── PokedexExplorer.csproj
├── ORM_presentation_CZ.md  # Project presentation in czech
├── ORM_presentation_EN.md  # Project presentation in english
├── TUTORIAL.md             # Step-by-step educational guide
├── TUTORIAL_CZ.md          # Step-by-step educational guide in czech
└── README.md               # project readme
```

## Key Features
- **Data Ingestion:** Custom script to fetch and reformat PokéAPI (NoSQL-like) data into PostgreSQL.
- **ORM Mastery:** Implementation of **Code-First** approach with Entity Framework.
- **Advanced Filtering:** Real-time search by Name, Type, Abilities, Moves, and physical stats.
- **Complex Modeling:** Handles 1:N and M:N relationships (Evolution chains, Pokémon-Move sets).

## Prerequisites
Before you begin, ensure you have the following installed on your system:
- **Operating System**: Windows 10/11, Ubuntu 20.04+, or macOS.
- **PostgreSQL 17**: A relational database server to store Pokémon data. Download [here](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads)
- **Visual Studio 2022**: With the **.NET Desktop Development** workload installed (for WPF support). You can download from this [page](https://visualstudio.microsoft.com/cs/)
- **.NET 9.0 SDK**: The latest .NET runtime and software development kit. It will be downloaded with Visual Studio

## Quick Start
### 1. Database initialization
To set up a new localized database cluster for this project, follow these steps:
- Open your terminal or command prompt.  
- Navigate to your PostgreSQL `bin` directory (on Windows usually `C:\Program Files\PostgreSQL\17\bin`).
```bash
cd C:\Program Files\PostgreSQL\17\bin
```

- Run the following command to start to databaze from project folder:
```bash
pg_ctl start -D <your_repository_path>\pokemondb\
```
- Ensure PostgreSQL is running (default port 5432 or update `PokemonDbContext`).

### Database configuration (if needed)
**1. Adjusting Port and Credentials**

In the `Data/PokemonDbContext.cs` file, locate the OnConfiguring method. You need to set the parameters here to match your PostgreSQL setup:

```csharp
protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder) {
    // Host: Server address (use 'localhost' for your local PC)
    // Port: In this tutorial, we use 5433 (the standard default is 5432)
    // Username/Password: Credentials chosen during installation (e.g., postgres/postgres)
    optionsBuilder.UseNpgsql("Host=localhost;Port=5433;Username=postgres;Password=postgres;Database=postgres;");
}
```

## Building and Running the Project
You can build and run the application in visual studio or directly from the command line using the .NET CLI.:
1. Open a Windows PowerShell terminal in the root directory of the repository.
2. Execute the following command in console:
```powershell
dotnet run --project .\PokedexExplorer\PokedexExplorer.csproj
```
or 
```powershell
dotnet run --project <your_repository_path>\PokedexExplorer\PokedexExplorer.csproj
```

What happens during `dotnet run`:
- **Restore:** The system automatically downloads all required **NuGet dependencies** (Npgsql, EF Core, etc.).
- **Build:** Compiles the C# code into an executable application.
- **Execution:** Launches the **Pokedex Explorer WPF** window.

> Now you can enjoy your pokemon exploring.

## Learn with this Project
Here is a comprehensive educational, step-by-step tutorial for anyone who wants to learn how to build this from scratch:

### [ Read the Full Step-by-Step Tutorial here](TUTORIAL.md)

## Disclaimer & Attribution
*Educational project only. Not affiliated with Nintendo/The Pokémon Company.*
- **Data:** [PokéAPI](https://pokeapi.co/) (BSD 3-Clause License).
- **Sprites:** Owned by Nintendo, used here under educational fair use.

# Library Management System (ASP.NET Core MVC, No Database)

A tiny Library Management System built with **ASP.NET Core MVC (.NET 8)**.
All data is stored **in-memory** (`Data/LibraryStore.cs`) using static
`List<T>` collections — there is no database, no Entity Framework, and no
connection string. Data resets whenever the app restarts, which is
expected behavior for this kind of mini/academic project.

## Features

- **Dashboard** — quick stats: total titles, total copies, members,
  books currently issued, overdue books.
- **Books** — full CRUD (Create, Read, Update, Delete) + search by
  title/author/category. Tracks total vs. available copies.
- **Members** — full CRUD for library members (MCA students), with a
  per-member issue history.
- **Issue / Return** — issue an available book to a member (auto sets a
  14-day due date), mark a book as returned, and see overdue status.

## Project Structure

```
LibraryManagementSystem/
├── Controllers/
│   ├── HomeController.cs
│   ├── BooksController.cs
│   ├── MembersController.cs
│   └── IssuesController.cs
├── Models/
│   ├── Book.cs
│   ├── Member.cs
│   └── IssueRecord.cs
├── Data/
│   └── LibraryStore.cs        <- in-memory "database"
├── Views/
│   ├── Home/, Books/, Members/, Issues/, Shared/
├── wwwroot/css/site.css
├── Program.cs
├── appsettings.json
└── LibraryManagementSystem.csproj
```

## How to Run

1. Install the [.NET 8 SDK](https://dotnet.microsoft.com/download) if
   you don't already have it.
2. Open a terminal in the `LibraryManagementSystem` folder.
3. Restore & run:
   ```
   dotnet restore
   dotnet run
   ```
4. Open the URL shown in the terminal (usually
   `https://localhost:5001` or `http://localhost:5000`) in your browser.

Alternatively, open `LibraryManagementSystem.csproj` in **Visual
Studio** or **Visual Studio Code** (with the C# extension) and press
Run/F5.

## Notes for Viva / Submission

- **No database** is used intentionally — data lives in static
  in-memory collections (`LibraryStore`), which simulates persistence
  for the duration the app is running. This keeps the project simple
  and dependency-free, ideal for a quick demo/mini-project.
- To extend this into a full project, you could swap `LibraryStore`
  for Entity Framework Core + SQL Server/SQLite without changing the
  controllers much, since the store is accessed through a single
  static class.
- Sample data (a few books and members) is pre-seeded so the app has
  content to show immediately on first run.

## Possible Extensions

- Add authentication (Admin/Student login) using ASP.NET Core Identity.
- Persist data to a database (SQLite is easiest to add) or to a JSON
  file on disk.
- Add fines calculation for overdue books.
- Add pagination and sorting to the Books/Members list.

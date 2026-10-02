# Techwatchers

A community forum for tech enthusiasts. Users can create an account, publish posts in categories, and like and comment on other people's posts.

## Features

- **Registration and login** with server-side sessions and input validation (username format, email format, strong password rules)
- **Posts** with titles, descriptions and categories
- **Forum feed** for browsing posts from all users
- **Likes and comments** on individual posts
- **User profile** with the ability to change the password
- **Database migrations** with Entity Framework Core

## Tech stack

| Layer        | Technologies                               |
| ------------ | ------------------------------------------ |
| Frontend     | Angular 19, TypeScript, Bootstrap 5        |
| Backend      | ASP.NET Core 8 (C#), Entity Framework Core |
| Database     | MySQL                                      |
| Architecture | REST API, repository pattern               |

## Getting started

### Prerequisites

- .NET 8 SDK
- Node.js 20+
- MySQL Server
- EF Core CLI: `dotnet tool install --global dotnet-ef`

### 1. Clone the repository

```bash
git clone https://github.com/kajetanszlenzak/techwatchers.git
cd techwatchers
```

### 2. Configure the database

Set your MySQL connection string in `Techwatchers.Server/appsettings.Development.json`:

```json
"ConnectionStrings": {
  "MySqlConnection": "Server=localhost;Database=techwatchers;User=root;Password=YOUR_PASSWORD;"
}
```

### 3. Install dependencies and create the database

```bash
cd techwatchers.client
npm install --force

cd ../Techwatchers.Server
dotnet ef database update
```

### 4. Run

```bash
# from Techwatchers.Server; starts the API and the Angular dev server together
dotnet run
```

## API overview

| Method | Endpoint                       | Description            |
| ------ | ------------------------------ | ---------------------- |
| POST   | `/api/register`                | Create an account      |
| POST   | `/api/login`                   | Sign in                |
| POST   | `/api/login/logout`            | Log out                |
| GET    | `/api/posts`                   | List posts             |
| POST   | `/api/posts`                   | Create a post          |
| GET    | `/api/posts/{id}`              | Get a post             |
| POST   | `/api/posts/{id}/toggle-like`  | Like or unlike a post  |
| GET    | `/api/posts/{id}/comments`     | List comments          |
| POST   | `/api/posts/{id}/comments`     | Add a comment          |
| GET    | `/api/profile/current-user`    | Get the signed-in user |
| POST   | `/api/profile/update-password` | Change the password    |

<!-- TODO: double-check that each endpoint is on the right controller -->

## Project structure

```
techwatchers/
├── Techwatchers.Server/     # ASP.NET Core 8 API
│   ├── Controllers/
│   ├── Models/
│   ├── Repositories/
│   ├── Migrations/          # EF Core migrations
│   └── Program.cs
└── techwatchers.client/     # Angular 19 app
    └── src/app/             # forum, post-details, profile, login, register...
```

Full technical documentation (in Polish), including data models, is available in [`dokumentacja.html`](dokumentacja.html).

## Authors

Built by **Kajetan Szlenzak** ([Portfolio](https://kajetanszlenzak.github.io) · [LinkedIn](https://www.linkedin.com/in/kajetan-szlenzak-b7473a26a/)) and **Dawid Gulczyński**.

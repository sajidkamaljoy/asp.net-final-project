# Society Management (ASP.NET final project, early version)
[![CI](https://github.com/sajidkamaljoy/asp.net-final-project/actions/workflows/ci.yml/badge.svg)](https://github.com/sajidkamaljoy/asp.net-final-project/actions/workflows/ci.yml)

An earlier iteration of the society management REST API. It focuses on tenants, repair requests and security staff shifts. The more complete, later version is in the repo `SocietyManagement`.

## Solution layout

| Project | Responsibility |
|---|---|
| `Society Management` | ASP.NET Web API 2 layer with `Manager` and `Security` controllers |
| `bll` | Business logic: services and DTOs (tenant, repair, shift, security report) |
| `dal` | Entity Framework 6 code-first models (`SMContext`), repositories and migrations |

## API overview

Every resource follows the same pattern:

```
GET    api/{resource}            list all
GET    api/{resource}/{id}       get one
POST   api/{resource}/add        create
PUT    api/{resource}/update     update
DELETE api/{resource}/delete/{id}
```

Resources: `tenant` (plus `api/tenant/repair/{id}` for a tenant's repairs), `repair`, `security` (plus `api/security/{id}/reports`) and `shift`.

## Tech stack

ASP.NET Web API 2, C#, .NET Framework 4.7.2, Entity Framework 6 (code-first with migrations), SQL Server.

## Run it

1. Open `Society Management/Society Management.sln` in Visual Studio and restore NuGet packages.
2. `Society Management/Web.config` is git-ignored and not in this repo, so create one (the Web API template's default works) and add a connection string for the `SMContext` database on your SQL Server instance.
3. Run `Update-Database` in the Package Manager Console (default project `dal`) to create the schema from the included migrations.
4. Set `Society Management` as the startup project and press F5.

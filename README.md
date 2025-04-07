
# 🧱 Hexagonal Architecture in .NET — The Master Guide

## 📑 Table of Contents

1. [Hexagonal Architecture Explained](#hexagonal-architecture-explained)
2. [What is it?](#what-is-it)
3. [Analysis of the First Diagram (Hexagon Model)](#analysis-of-the-first-diagram-hexagon-model)
    - [Diagram Parts](#diagram-parts)
    - [Flow](#flow)
4. [Analysis of the Second Diagram (Use Case: Update User)](#analysis-of-the-second-diagram-use-case-update-user)
    - [Use Case Flow](#use-case-flow)
    - [Technical Highlights](#technical-highlights)
5. [Pros and Cons](#pros-and-cons)
    - [Pros](#pros)
    - [Cons](#cons)
6. [Best Practices and Practical Advice](#best-practices-and-practical-advice)
7. [Real Example Setup](#real-example-setup)
8. [Core Features](#core-features)
9. [Advantages](#advantages)
10. [Disadvantages](#disadvantages)
11. [Key Highlights in .NET](#key-highlights-in-net)
12. [GitHub Repositories](#github-repositories)
13. [Recommended Books](#recommended-books)
14. [Articles and Blogs](#articles-and-blogs)
15. [How to Become a Hexagonal Architecture Expert in .NET](#how-to-become-a-hexagonal-architecture-expert-in-net)
16. [Pro Tips](#pro-tips)
17. [Project Layers](#project-layers)

---

## Hexagonal Architecture Explained

Hexagonal Architecture (a.k.a. Ports and Adapters) separates the business logic from external systems. It enhances testability, modularity, and adaptability to changes.

## What is it?

A pattern where:

- The **Core** is the business logic.
- **Ports** are interfaces defining inputs and outputs.
- **Adapters** are concrete implementations (e.g., database, REST API).
- External systems plug into the core via adapters, not directly.

---

## Analysis of the First Diagram (Hexagon Model)

### Diagram Parts

- **Core (Negocio):** Pure business logic.
- **Port:** Interfaces used by the core.
- **Adapter:** Concrete implementation.
- **Entity Framework:** Example of a DB adapter.
- **Infra:** Infrastructure layer.

### Flow

1. Core defines interfaces.
2. Infrastructure implements them.
3. Adapters connect the interfaces with external systems.

---

## Analysis of the Second Diagram (Use Case: Update User)

### Use Case Flow

1. Controller receives the request.
2. Use Case reads the user.
3. Validations are executed.
4. User is updated and saved.
5. Adapters handle database operations.
6. Mappers convert between DTO, domain, and persistence models.

### Technical Highlights

- `IDatabase` interfaces enable decoupling.
- Mappers prevent leakage between layers.
- Adapters isolate framework-specific code.

---

## Pros and Cons

### Pros

- High testability via interfaces.
- Separation of concerns.
- Framework-independent core.
- Easy to switch implementations.

### Cons

- More boilerplate code.
- Risk of overengineering.
- Requires proper naming and layer separation.

---

## Best Practices and Practical Advice

- Split use cases into separate classes.
- Avoid God Repositories.
- Define ports per use case.
- Keep adapters dumb and focused.
- Write unit tests by mocking interfaces.

---

## Real Example Setup

We can build a .NET solution using:

- **EF Core Adapter**
- **Domain Layer**
- **Application Layer (use cases)**
- **API Controllers**
- **Dependency Injection**

---

## Core Features

| Feature                     | Description                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| Separation of Concerns     | Core logic is decoupled from infrastructure                                 |
| Port/Adapter Pattern        | Interfaces (ports) and implementations (adapters)                          |
| Testability                | Core can be unit tested with mocks                                          |
| Independence               | Core doesn't depend on frameworks                                           |
| Scalability                | Modular structure supports growing needs                                    |

---

## Advantages

- Clean codebase structure.
- Test-driven development enabled.
- Interface-based mocking.
- Framework-agnostic design.

---

## Disadvantages

- Verbose codebase.
- Harder for juniors to grasp.
- Mapping layers add complexity.

---

## Key Highlights in .NET

- Use interfaces like `IUserRepository`.
- Place business logic in Application/Core.
- Inject dependencies using built-in DI.
- Apply CQRS with MediatR.
- Combine with Clean Architecture and DDD.

---

## GitHub Repositories

| Repository | Description |
|------------|-------------|
| [jasontaylordev/CleanArchitecture](https://github.com/jasontaylordev/CleanArchitecture) | Production-ready Clean Architecture template |
| [ardalis/CleanArchitecture](https://github.com/ardalis/CleanArchitecture) | Clean layering by Ardalis |
| [manelferreira/HexagonalArchitectureDotNet](https://github.com/manelferreira/HexagonalArchitectureDotNet) | Sample hexagonal app |
| [albertodotnet/HexagonalArchitecture](https://github.com/albertodotnet/HexagonalArchitecture) | Educational structure |

---

## Recommended Books

- "Implementing Domain-Driven Design" – Vaughn Vernon
- "Clean Architecture" – Robert C. Martin
- "Hands-On DDD with .NET Core" – Alexey Zimarev
- "Architecture Patterns with .NET" – Dino Esposito

---

## Articles and Blogs

- [Hexagonal Architecture with .NET Core](https://medium.com/@andres_urrego/hexagonal-architecture-with-net-core-2a1b5b00d5b5)
- [Ports and Adapters Explained](https://herbertograca.com/2017/09/14/ports-adapters-architecture/)
- [Microsoft DevBlog – Hexagonal Architecture](https://devblogs.microsoft.com/)

---

## How to Become a Hexagonal Architecture Expert in .NET

### Phase 1: Fundamentals
- Learn SOLID principles
- Understand interfaces and DI

### Phase 2: Intermediate Projects
- CRUD operations with mapping
- Apply EF Core adapters

### Phase 3: Advanced
- CQRS + MediatR
- External service adapters

### Phase 4: Mastery
- Migrate monoliths to modular hexagonal structure
- Combine with DDD/Microservices/Event Sourcing

---

## Pro Tips

- Prefix ports with `I`.
- Avoid shared models across layers.
- Group use cases by responsibility.
- Inject only needed dependencies.
- Prefer constructor injection.

---

## Project Layers

- **EF Core Adapter:** Implements persistence.
- **Domain Layer:** Contains entities and logic.
- **Application Layer:** Holds use cases.
- **API Controllers:** Handle HTTP communication.
- **Dependency Injection:** Configures adapters via interfaces.

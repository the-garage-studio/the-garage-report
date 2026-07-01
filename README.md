# The Garage Report

**Author:** Alonso Enrique Higa Kohatsu

**Status:** In development

**Last updated:** 30 June 2026

---

## Table of Contents

- [Introduction](#introduction)
- [Vision](#vision)
- [Project Scope](#project-scope)

---

## **Introduction**
This project was born from an idea I had in mind for a long time. I grew up playing FIFA, and one of the game's standout features that always caught my attention was the transfer market its a dynamic built around buying, selling, and collecting unique players. From that idea came this project: a market for car cards, where each card represents a unique, one-of-a-kind car model, similar to a collectible card. Users can decide what to do with their card, whether to sell it or collect it, and most importantly, **CARDS ARE UNIQUE**.

The car theme was an intentional choice. I wanted an excuse to learn more about car models, brands, and characteristics from the automotive world, while building a project that combined something I was genuinely motivated by with the opportunity to strengthen and demonstrate technical skills as a backend developer and software engineer.

This project doesn't aim to solve a specific problem, but rather to bring to life an idea I've had for a while, thanks to what I've learned throughout my degree, I can now build following good practices, proving that what I learn can be applied in practice.

## **Vision**

The project aims to become a functional platform for trading car cards, replicating an experience similar to a FIFA-style transfer market, but applied to an automotive theme.

Additionally, the development of this project has the personal and professional purpose of demonstrating proficiency in:

* Architecture design and diagramming using the C4 model
* Backend development with Java and Spring Boot, applying DDD and design patterns
* Deployment automation with GitHub Actions
* Cloud deployment using Azure
* Application containerization with Docker
* Sizing and estimating infrastructure costs in a production environment

## **Project Scope**

### 1. Frontend Scope

- **Design**
  - The application will feature a responsive design, adapting to different screen sizes (desktop and mobile).
  - Although the visual aspect is important for making the application easy to understand, it is not the primary focus of this project.

- **Best Practices**
  - Industry-standard frontend best practices and design patterns (componentization, separation of concerns) will be applied, although not with the same level of depth as the backend.

- **State Management**
  - The use of a simple state management solution (Angular Signals) will be evaluated if the application's data flow justifies it.

- **Componentization**
  - The user interface will be structured into reusable components, promoting a clear separation between presentation and business logic.

- **Mock API**
  - To avoid the cost of keeping the backend running permanently, the frontend will consume a mock API based on a `db.json` file, simulating the behavior of a real REST API (using `json-server`).

- **Internationalization (i18n)**
  - Multi-language support will be evaluated, not as a critical project requirement, but as an additional demonstration of best practices.

#### Out of Scope

- End-to-end (E2E) testing.
- Advanced performance optimization (aggressive lazy loading, SSR / Angular Universal).
- Professional-level accessibility (WCAG).

---

### 2. Backend Scope

- **Security**
  - Basic security will be implemented using Spring Security with JWT (JSON Web Token) authentication.

- **Architecture**
  - A modular monolith architecture will be adopted.
  - This decision is intentional: given the size and limited domain of this project (cards, users, transactions), a modular monolith following DDD principles is more appropriate than a distributed architecture (microservices), which would introduce unnecessary complexity without providing meaningful value.

- **Design Patterns and DDD**
  - Design patterns and Domain-Driven Design (DDD) principles will be applied, including a clear separation of layers (Domain, Application, Infrastructure), as well as tactical patterns such as Value Objects, Aggregates, and Domain Events where appropriate.

- **Code Documentation**
  - The codebase will include clear documentation (comments where necessary and consistent naming conventions), along with API documentation using Swagger / OpenAPI.

- **Testing**
  - Unit tests (JUnit, Mockito) will be included, along with integration tests for the main domain workflows whenever possible.

- **Error Handling**
  - A centralized exception handling layer (`@ControllerAdvice`) will be implemented to ensure consistent error responses.

- **Persistence**
  - The database engine (PostgreSQL or MySQL) will be defined.

#### Out of Scope

- Microservices or distributed architectures.
- Asynchronous messaging (Kafka, RabbitMQ).
- Multi-tenancy.
- Advanced rate limiting or a dedicated API Gateway.
- Advanced observability (Prometheus, Grafana), considered as a possible future extension.

---

### 3. Deployment & Infrastructure Scope

- **Deployment Evidence**
  - A video will be recorded documenting the deployment process to Azure, demonstrating that the application was successfully deployed from a local environment to production.

- **Post-Deployment Shutdown**
  - After recording the deployment evidence, the backend instances and Azure infrastructure will be removed to avoid unnecessary costs.
  - Only the frontend will remain online, deployed on GitHub Pages (or a similar platform), consuming the mock API included within the frontend codebase.

- **CI/CD**
  - A continuous integration and deployment pipeline will be implemented using GitHub Actions, including build, testing, and automated deployment stages.

- **Containerization**
  - The backend application will be containerized using Docker, and the image may be published to a container registry (Docker Hub or Azure Container Registry) as part of the deployment process.

- **Cost Estimation**
  - An estimated infrastructure cost analysis will be documented (for example, comparing different Azure App Service tiers or virtual machine options) in case the project were to run in a real production environment.

- **Basic Cloud Security**
  - Proper management of environment variables and secrets (without hardcoding credentials), HTTPS usage, and basic network security group (NSG) configuration if a virtual machine is used.

#### Out of Scope

- High availability (multi-zone deployment, load balancing).
- Auto-scaling.
- Continuous production monitoring (24/7).
- Automated backups.
- Long-term production infrastructure maintenance (the deployment is for demonstration purposes, not permanent production use).

---

### 4. Product / Application Scope

- **User Management**
  - User registration.
  - User login.
  - User profile.

- **Card Management**
  - Cards will be created exclusively by the system, meaning users cannot create their own cards.
  - Cards will be generated by an administrator.
  - At predefined intervals (to be determined), users will be able to open a free pack containing a randomly assigned card.

- **Marketplace / Trading**
  - List a card for sale.
  - Purchase a card.
  - Transaction history.
  - Marketplace search.
  - Filter-based search.

- **Card Uniqueness**
  - Once a user purchases a card, they become its sole owner since every card is unique.
  - If the owner no longer wants the card, they may list it for sale again.
  - If an administrator determines that certain cards are never purchased, they may remove them from circulation by changing their status (to "inactive") instead of deleting them from the database.
  - Cards may have different rarity levels, such as **Special** or **Legendary**.
  - Once a card's rarity has been assigned, it cannot be changed, and its value will not depreciate. The rarity and card type remain permanent.

- **Personal Collection**
  - Users can view all the cards stored in their collection.
  - Users can filter their collection by brand, purchase price, or current value.
  - Users can store up to a certain number of cards in their collection. If they wish to increase this limit, they will need to purchase a subscription plan.

- **Roles**
  - Different roles will exist, such as Administrator, Developer, and Regular User.

#### Out of Scope (Product)

- Real-time auctions between users.
- Chat or direct messaging between users.
- Direct card trading between users (outside the marketplace).
- Friends or user-following system.
- Collector rankings or leagues.
- Native mobile application.
- Integration with real money or payment gateways.
- Purchasing card packs with real money.
- Cross-server or cross-region marketplace.
- Advanced user profile customization.
- User-created cards.
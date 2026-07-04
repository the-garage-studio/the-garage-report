# The Garage Report

**Author:** Alonso Enrique Higa Kohatsu

**Status:** In development

**Last updated:** 2 July 2026

---

## Table of Contents

1. [Project Overview](#project-overview)
   - [1.1. Introduction](#introduction)
   - [1.2. Vision](#vision)
   - [1.3. Project Scope](#project-scope)
     - [1.3.1. Frontend Scope](#1-frontend-scope)
     - [1.3.2. Backend Scope](#2-backend-scope)
     - [1.3.3. Deployment & Infrastructure Scope](#3-deployment--infrastructure-scope)
     - [1.3.4. Product / Application Scope](#4-product--application-scope)

2. [Requirements Specification](#requirements-specification)
   - [2.1. Epics](#epics)
   - [2.2. User Stories](#user-stories)
   - [2.3. Technical Stories](#technical-stories)


---
## **Project Overview**

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

## **Requirements Specification**

## **Epics**

<table>
  <thead>
    <tr>
      <th>ID</th>
      <th>Epic</th>
      <th>Description</th>
      <th>Derived From</th>
      <th>Acceptance Criteria</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>EPIC-01</td>
      <td>User Management & Authentication</td>
      <td>User registration, authentication, profile management, and platform security.</td>
      <td>User Management, Backend Security</td>
      <td>
        Given that a new user provides valid registration information,<br>
        When the registration request is submitted,<br>
        Then the system creates a new user account successfully.<br><br>
        Given that a registered user provides valid credentials,<br>
        When the user logs in,<br>
        Then the system authenticates the user and issues a valid JWT.<br><br>
        Given that an authenticated user accesses their profile,<br>
        When the request is authorized,<br>
        Then the system returns the user's profile information.
      </td>
    </tr>
    <tr>
      <td>EPIC-02</td>
      <td>Card Catalog Administration</td>
      <td>Administration of the card catalog, including creation, rarity assignment, and circulation management.</td>
      <td>Card Management, Card Uniqueness</td>
      <td>
        Given that an administrator creates a new card,<br>
        When all required information is provided,<br>
        Then the card is stored in the catalog.<br><br>
        Given that a card exists,<br>
        When the administrator updates its status,<br>
        Then the card becomes active or inactive accordingly.<br><br>
        Given that a card has an assigned rarity,<br>
        When it is saved,<br>
        Then its rarity cannot be modified afterwards.
      </td>
    </tr>
    <tr>
      <td>EPIC-03</td>
      <td>Card Pack Opening</td>
      <td>Free periodic packs and the random card generation process.</td>
      <td>Card Management</td>
      <td>
        Given that the cooldown period has expired,<br>
        When the user opens a free pack,<br>
        Then the system awards one random card.<br><br>
        Given that the user has already claimed the current pack,<br>
        When another attempt is made,<br>
        Then the system prevents opening a new pack until the cooldown expires.
      </td>
    </tr>
    <tr>
      <td>EPIC-04</td>
      <td>Marketplace & Trading</td>
      <td>Buying, selling, searching, filtering, and transaction history.</td>
      <td>Marketplace / Trading</td>
      <td>
        Given that a user owns a card,<br>
        When the user publishes it for sale,<br>
        Then the card becomes visible in the marketplace.<br><br>
        Given that another user purchases the card,<br>
        When the transaction is completed,<br>
        Then ownership is transferred and the transaction is recorded.<br><br>
        Given that cards exist in the marketplace,<br>
        When a user searches or filters them,<br>
        Then only matching results are displayed.
      </td>
    </tr>
    <tr>
      <td>EPIC-05</td>
      <td>Personal Card Collection</td>
      <td>User inventory, collection management, and filtering.</td>
      <td>Personal Collection</td>
      <td>
        Given that a user owns cards,<br>
        When the collection is opened,<br>
        Then all owned cards are displayed.<br><br>
        Given that filters are applied,<br>
        When the collection is refreshed,<br>
        Then only cards matching the selected criteria are shown.
      </td>
    </tr>
    <tr>
      <td>EPIC-06</td>
      <td>Subscription Plans</td>
      <td>Subscription plans that increase the user's collection storage limit.</td>
      <td>Personal Collection</td>
      <td>
        Given that a user reaches the storage limit,<br>
        When a subscription plan is activated,<br>
        Then the collection capacity is increased.<br><br>
        Given that no active subscription exists,<br>
        When the storage limit is reached,<br>
        Then the system prevents storing additional cards.
      </td>
    </tr>
    <tr>
      <td>EPIC-07</td>
      <td>Roles & Permissions</td>
      <td>Role-based authorization and permission management.</td>
      <td>Roles</td>
      <td>
        Given that a user has an assigned role,<br>
        When accessing a protected resource,<br>
        Then the system grants or denies access based on permissions.<br><br>
        Given that an administrator accesses administration features,<br>
        When the request is authorized,<br>
        Then the system allows administrative operations.
      </td>
    </tr>
  </tbody>
</table>

<br><br><br>

## **User Stories**

<table>
  <thead>
    <tr>
      <th>ID</th>
      <th>Title</th>
      <th>Description</th>
      <th>User Story</th>
      <th>Acceptance Criteria</th>
      <th>Epic</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>US01</td>
      <td>User Registration</td>
      <td>Allows new users to create an account using a unique email address and password.</td>
      <td>As a new user, I want to register an account with my email and password, so that I can access the platform and start using it.</td>
      <td>
        Given a visitor is on the registration page,<br>
        When they submit a valid unique email, password, and required fields,<br>
        Then the system creates the account and confirms success.<br><br>
        Given a visitor submits an email already in use,<br>
        When they attempt to register,<br>
        Then the system rejects the request with a clear error message.<br><br>
        Given a visitor submits a password that doesn't meet security requirements,<br>
        When they attempt to register,<br>
        Then the system rejects the request and indicates the missing requirements.
      </td>
      <td>EP01</td>
    </tr>
    <tr>
      <td>US02</td>
      <td>User Login</td>
      <td>Enables registered users to authenticate and securely access the application.</td>
      <td>As a registered user, I want to log in with my credentials, so that I can securely access my account and its features.</td>
      <td>
        Given a registered user enters valid credentials,<br>
        When they submit the login form,<br>
        Then the system authenticates them and issues a JWT token.<br><br>
        Given a user enters invalid credentials,<br>
        When they submit the login form,<br>
        Then the system displays a generic error without specifying which field is incorrect.
      </td>
      <td>EP01</td>
    </tr>
    <tr>
      <td>US03</td>
      <td>View and Edit Profile</td>
      <td>Allows users to view and update their personal profile information.</td>
      <td>As a registered user, I want to view and edit my profile information, so that I can keep my account details up to date.</td>
      <td>
        Given a logged-in user navigates to their profile,<br>
        When the page loads,<br>
        Then the system displays their current profile data.<br><br>
        Given a logged-in user updates an editable field,<br>
        When they save the changes,<br>
        Then the system persists the update and confirms success.
      </td>
      <td>EP01</td>
    </tr>
    <tr>
      <td>US04</td>
      <td>Create a New Card</td>
      <td>Enables administrators to create new collectible car cards with their corresponding attributes and rarity.</td>
      <td>As an administrator, I want to create new car cards with their attributes (model, brand, rarity), so that they become available for users to obtain.</td>
      <td>
        Given an administrator fills in brand, model, and rarity,<br>
        When they submit the form,<br>
        Then the system creates the card with "active" status.<br><br>
        Given a card has been created with an assigned rarity,<br>
        When any user attempts to modify that rarity afterward,<br>
        Then the system rejects the change.
      </td>
      <td>EP02</td>
    </tr>
    <tr>
      <td>US05</td>
      <td>Deactivate a Card</td>
      <td>Allows administrators to deactivate cards without deleting their historical records.</td>
      <td>As an administrator, I want to deactivate cards that are never purchased, so that they no longer circulate without deleting their historical data.</td>
      <td>
        Given an administrator selects an active, unpurchased card,<br>
        When they change its status to "inactive,"<br>
        Then the card no longer appears in the marketplace or in pack openings.<br><br>
        Given a card is deactivated,<br>
        When the action is completed,<br>
        Then the card record remains stored in the database (soft delete).
      </td>
      <td>EP02</td>
    </tr>
    <tr>
      <td>US06</td>
      <td>Open a Free Card Pack</td>
      <td>Enables users to periodically receive a random card by opening a free pack.</td>
      <td>As a regular user, I want to open a free card pack at defined intervals, so that I can obtain new cards for my collection.</td>
      <td>
        Given the defined time interval has passed since the user's last pack opening,<br>
        When the user opens a pack,<br>
        Then the system assigns one random active card to their collection.<br><br>
        Given the time interval has not yet passed,<br>
        When the user attempts to open a pack,<br>
        Then the system blocks the action and indicates the remaining wait time.
      </td>
      <td>EP03</td>
    </tr>
    <tr>
      <td>US07</td>
      <td>List a Card for Sale</td>
      <td>Allows card owners to publish their cards for sale in the marketplace.</td>
      <td>As a card owner, I want to list one of my cards for sale in the marketplace, so that other users can purchase it.</td>
      <td>
        Given a user owns a card,<br>
        When they set a sale price and list it,<br>
        Then the card's status changes to "for sale" and becomes visible in the marketplace.<br><br>
        Given a user does not own a card,<br>
        When they attempt to list it,<br>
        Then the system rejects the action.
      </td>
      <td>EP04</td>
    </tr>
    <tr>
      <td>US08</td>
      <td>Purchase a Card</td>
      <td>Enables users to purchase cards listed by other users and transfer ownership.</td>
      <td>As a user, I want to purchase a card that is listed in the marketplace, so that I can become its new owner.</td>
      <td>
        Given a card is listed for sale and the user is not its current owner,<br>
        When the user completes the purchase,<br>
        Then ownership transfers to the buyer and the card is removed from the marketplace.<br><br>
        Given a purchase is completed,<br>
        When the transaction finishes,<br>
        Then the system records it in the transaction history.
      </td>
      <td>EP04</td>
    </tr>
    <tr>
      <td>US09</td>
      <td>Search and Filter the Marketplace</td>
      <td>Allows users to search and filter marketplace listings based on different criteria.</td>
      <td>As a user, I want to search and filter cards available in the marketplace, so that I can quickly find cards that interest me.</td>
      <td>
        Given a user enters a search term (name, brand, or model),<br>
        When they submit the search,<br>
        Then the system displays matching results.<br><br>
        Given a user applies rarity or price range filters,<br>
        When the filters are applied,<br>
        Then the results update to reflect only matching cards.
      </td>
      <td>EP04</td>
    </tr>
    <tr>
      <td>US10</td>
      <td>View Personal Collection</td>
      <td>Enables users to browse and organize the cards they currently own</td>
      <td>As a user, I want to view all the cards in my personal collection, so that I can keep track of what I currently own.</td>
      <td>
        Given a logged-in user navigates to their collection,<br>
        When the page loads,<br>
        Then the system displays all cards they currently own with their main attributes.<br><br>
        Given a user applies a filter (brand, purchase price, or current value),<br>
        When the filter is applied,<br>
        Then the collection view updates accordingly.
      </td>
      <td>EP05</td>
    </tr>
    <tr>
      <td>US11</td>
      <td>View Transaction History</td>
      <td>Allows users to review a record of their past purchases and sales in the marketplace.</td>
      <td>As a user, I want to view my transaction history, so that I can keep track of the cards I have bought and sold.</td>
      <td>
        <ul>
          <li>Given a logged-in user navigates to their transaction history, when the page loads, then the system displays all past purchases and sales with date, price, and card details.</li>
          <li>Given a user has no completed transactions, when they open the transaction history, then the system displays an empty state message.</li>
        </ul>
      </td>
      <td>EP04</td>
    </tr>
    <tr>
      <td>US12</td>
      <td>Cancel a Card Listing</td>
      <td>Enables owners to remove their card from the marketplace before it is purchased.</td>
      <td>As a card owner, I want to cancel an active listing, so that I can keep the card in my collection instead of selling it.</td>
      <td>
        <ul>
          <li>Given a user has a card listed for sale that has not been purchased, when they cancel the listing, then the card's status returns to <strong>owned</strong> and it is removed from the marketplace.</li>
          <li>Given a card has already been purchased by another user, when the original owner attempts to cancel the listing, then the system rejects the action.</li>
        </ul>
      </td>
      <td>EP04</td>
    </tr>
    <tr>
      <td>US13</td>
      <td>View Remaining Pack Cooldown</td>
      <td>Shows users how much time remains before they can open their next free pack.</td>
      <td>As a regular user, I want to see the remaining cooldown time before my next free pack, so that I know when I can open it again.</td>
      <td>
        <ul>
          <li>Given a user has already opened a pack within the current cooldown period, when they visit the pack-opening screen, then the system displays the exact time remaining until the next pack is available.</li>
          <li>Given the cooldown period has expired, when the user visits the pack-opening screen, then the system indicates that a new pack is ready to be opened.</li>
        </ul>
      </td>
      <td>EP03</td>
    </tr>
    <tr>
      <td>US14</td>
      <td>Subscribe to a Plan</td>
      <td>Allows users to purchase a subscription plan to increase their collection storage limit.</td>
      <td>As a user, I want to subscribe to a plan, so that I can store more cards in my personal collection.</td>
      <td>
        <ul>
          <li>Given a user selects an available subscription plan, when they confirm the subscription, then the system activates the plan and increases the user's storage limit accordingly.</li>
          <li>Given a user already has an active subscription, when they attempt to subscribe again, then the system prevents duplicate active subscriptions.</li>
        </ul>
      </td>
      <td>EP06</td>
    </tr>
    <tr>
      <td>US15</td>
      <td>View Active Subscription Details</td>
      <td>Enables users to check the status and benefits of their current subscription plan.</td>
      <td>As a subscribed user, I want to view my current plan's details, so that I know my storage limit and renewal information.</td>
      <td>
        <ul>
          <li>Given a user has an active subscription, when they open their subscription details, then the system displays the plan name, storage limit, and status.</li>
          <li>Given a user has no active subscription, when they open the subscription section, then the system displays the default storage limit and available plans to upgrade.</li>
        </ul>
      </td>
      <td>EP06</td>
    </tr>
    <tr>
      <td>US16</td>
      <td>Cancel a Subscription Plan</td>
      <td>Allows users to cancel their current subscription plan.</td>
      <td>As a subscribed user, I want to cancel my subscription plan, so that I stop being charged and my storage limit returns to default at the end of the billing period.</td>
      <td>
        <ul>
          <li>Given a user has an active subscription, when they request cancellation, then the system marks the subscription as <strong>cancelled</strong> and schedules the storage limit to revert once the current period ends.</li>
          <li>Given a user has no active subscription, when they attempt to cancel, then the system rejects the action.</li>
        </ul>
      </td>
      <td>EP06</td>
    </tr>
    <tr>
      <td>US17</td>
      <td>Assign Role to a User</td>
      <td>Enables administrators to assign a specific role (Administrator, Developer, Regular User) to a given user.</td>
      <td>As an administrator, I want to assign roles to users, so that I can control what actions they are authorized to perform.</td>
      <td>
        <ul>
          <li>Given an administrator selects a user and a valid role, when they confirm the assignment, then the system updates the user's role accordingly.</li>
          <li>Given a non-administrator attempts to assign a role, when the request is submitted, then the system rejects the action due to insufficient permissions.</li>
        </ul>
      </td>
      <td>EP07</td>
    </tr>
    <tr>
      <td>US18</td>
      <td>Restrict Access to Protected Resources</td>
      <td>Ensures that only users with the appropriate role can access certain features or endpoints.</td>
      <td>As a system, I want to restrict access to protected resources based on user roles, so that only authorized users can perform sensitive actions.</td>
      <td>
        <ul>
          <li>Given a user without the required role attempts to access a protected resource, when the request is made, then the system denies access and returns an authorization error.</li>
          <li>Given a user with the required role accesses the same resource, when the request is made, then the system grants access.</li>
        </ul>
      </td>
      <td>EP07</td>
    </tr>
    <tr>
      <td>US19</td>
      <td>View Card Details</td>
      <td>Allows any user to view the full details of a specific card, including brand, model, rarity, and current status.</td>
      <td>As a user, I want to view the detailed information of a card, so that I can decide whether to buy or keep it.</td>
      <td>
        <ul>
          <li>Given a card exists in the catalog, when a user selects it, then the system displays its brand, model, rarity, status, current owner (if applicable), and price (if listed).</li>
          <li>Given a card is inactive, when a regular user attempts to view it, then the system indicates that the card is not currently available.</li>
        </ul>
      </td>
      <td>EP02</td>
    </tr>
    <tr>
      <td>US20</td>
      <td>Reactivate a Deactivated Card</td>
      <td>Allows administrators to bring a previously deactivated card back into circulation.</td>
      <td>As an administrator, I want to reactivate a deactivated card, so that it becomes available again in the marketplace and pack openings.</td>
      <td>
        <ul>
          <li>Given a card has an <strong>inactive</strong> status, when an administrator changes its status to <strong>active</strong>, then the card becomes available again for packs and marketplace listings.</li>
          <li>Given a card is already active, when an administrator attempts to reactivate it, then the system indicates no change was needed.</li>
        </ul>
      </td>
      <td>EP02</td>
    </tr>
  </tbody>
</table>
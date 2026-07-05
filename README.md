# The Garage Report

**Author:** Alonso Enrique Higa Kohatsu

**Status:** In development

**Last updated:** 2 July 2026

---

## Table of Contents

- [The Garage Report](#the-garage-report)
  - [Table of Contents](#table-of-contents)
  - [**Project Overview**](#project-overview)
  - [**Introduction**](#introduction)
  - [**Vision**](#vision)
  - [**Project Scope**](#project-scope)
    - [1. Frontend Scope](#1-frontend-scope)
      - [Out of Scope](#out-of-scope)
    - [2. Backend Scope](#2-backend-scope)
      - [Out of Scope](#out-of-scope-1)
    - [3. Deployment \& Infrastructure Scope](#3-deployment--infrastructure-scope)
      - [Out of Scope](#out-of-scope-2)
    - [4. Product / Application Scope](#4-product--application-scope)
      - [Out of Scope (Product)](#out-of-scope-product)
  - [**Requirements Specification**](#requirements-specification)
  - [**Epics**](#epics)
  - [**User Stories**](#user-stories)
  - [**Domain Requirements**](#domain-requirements)
    - [Block 1: User Management \& Authentication](#block-1-user-management--authentication)
    - [Block 2: Card Catalog](#block-2-card-catalog)
    - [Block 3: Pack Opening](#block-3-pack-opening)
    - [Block 4: Marketplace / Transactions](#block-4-marketplace--transactions)
    - [Block 5: Personal Collection](#block-5-personal-collection)
    - [Block 6: Subscriptions](#block-6-subscriptions)


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
    <tr>
      <td>US21</td>
      <td>Password Recovery</td>
      <td>Allows users who forgot their password to reset it securely via email.</td>
      <td>As a registered user, I want to recover my account through a password reset process, so that I can regain access if I forget my password.</td>
      <td>
        <ul>
          <li>Given a user requests a password reset with a registered email, when the request is submitted, then the system sends a reset link/token to that email.</li>
          <li>Given a user follows a valid, non-expired reset link, when they submit a new password meeting security requirements, then the system updates the password and invalidates the reset token.</li>
          <li>Given a reset token has expired or was already used, when the user attempts to use it again, then the system rejects the request.</li>
        </ul>
      </td>
      <td>EP01</td>
    </tr>
    <tr>
      <td>US22</td>
      <td>Log Out</td>
      <td>Enables users to securely end their authenticated session.</td>
      <td>As a logged-in user, I want to log out of my account, so that my session is closed and my account stays secure on shared devices.</td>
      <td>
        <ul>
          <li>Given a logged-in user selects <strong>Log out</strong>, when the action is confirmed, then the system invalidates the current session/token and redirects to the login page.</li>
          <li>Given a session has already been closed, when a request is made using the old token, then the system rejects it as unauthorized.</li>
        </ul>
      </td>
      <td>EP01</td>
    </tr>
    <tr>
      <td>US23</td>
      <td>Account Deactivation</td>
      <td>Allows a user to deactivate their own account without permanently deleting their data.</td>
      <td>As a registered user, I want to deactivate my account, so that I can stop using the platform while keeping my data preserved.</td>
      <td>
        <ul>
          <li>Given a logged-in user requests account deactivation, when they confirm the action, then the system marks the account as <strong>inactive</strong> and logs the user out.</li>
          <li>Given an inactive account attempts to log in, when the credentials are correct, then the system denies access and informs the user their account is deactivated.</li>
        </ul>
      </td>
      <td>EP01</td>
    </tr>
    <tr>
      <td>US24</td>
      <td>Prevent Duplicate Card Purchase</td>
      <td>Ensures that a card cannot be purchased by two users simultaneously.</td>
      <td>As a system, I want to prevent concurrent purchases of the same card, so that only one user ends up owning it and data integrity is preserved.</td>
      <td>
        <ul>
          <li>Given two users attempt to purchase the same listed card at nearly the same time, when both requests are processed, then only the first completed transaction succeeds and the second is rejected with a clear message.</li>
          <li>Given a purchase attempt fails due to concurrency, when the user retries, then the system reflects the card's current real status (sold or still listed).</li>
        </ul>
      </td>
      <td>EP04</td>
    </tr>
    <tr>
      <td>US25</td>
      <td>Sort Marketplace Results</td>
      <td>Allows users to order marketplace listings by different criteria.</td>
      <td>As a user, I want to sort marketplace results by price, rarity, or listing date, so that I can find relevant cards more easily.</td>
      <td>
        <ul>
          <li>Given a user is viewing marketplace results, when they select a sorting criterion (e.g., price ascending, rarity, newest first), then the system reorders the results accordingly.</li>
          <li>Given no sorting criterion is selected, when the marketplace loads, then results are displayed in the default order (e.g., newest listings first).</li>
        </ul>
      </td>
      <td>EP04</td>
    </tr>
    <tr>
      <td>US26</td>
      <td>Bulk Card Creation</td>
      <td>Allows administrators to create multiple cards at once via a batch upload.</td>
      <td>As an administrator, I want to create multiple cards in bulk (e.g., via file upload), so that I can populate the catalog more efficiently.</td>
      <td>
        <ul>
          <li>Given an administrator uploads a valid batch file with card data, when the file is processed, then the system creates all valid cards and reports the number successfully added.</li>
          <li>Given the batch file contains invalid or incomplete entries, when the file is processed, then the system rejects only the invalid entries and reports which ones failed and why.</li>
        </ul>
      </td>
      <td>EP02</td>
    </tr>
    <tr>
      <td>US27</td>
      <td>View Card Catalog Statistics</td>
      <td>Provides administrators with an overview of the card catalog's composition and activity.</td>
      <td>As an administrator, I want to view statistics about the card catalog (total cards, active/inactive, rarity distribution), so that I can make informed decisions about circulation.</td>
      <td>
        <ul>
          <li>Given cards exist in the catalog, when an administrator opens the statistics dashboard, then the system displays counts by status and rarity, and identifies cards never purchased.</li>
          <li>Given the catalog has no cards, when the dashboard loads, then the system displays an empty/zeroed state.</li>
        </ul>
      </td>
      <td>EP02</td>
    </tr>
    <tr>
      <td>US28</td>
      <td>Notify User on Pack Availability</td>
      <td>Informs users when their free pack cooldown has ended and a new pack is ready.</td>
      <td>As a regular user, I want to be notified when my free pack is ready to open, so that I don't forget to claim it.</td>
      <td>
        <ul>
          <li>Given a user's pack cooldown has just expired, when they next access the platform, then the system displays a notification indicating a free pack is available.</li>
          <li>Given a user already claimed the pack for the current cycle, when they access the platform, then no availability notification is shown.</li>
        </ul>
      </td>
      <td>EP03</td>
    </tr>
    <tr>
      <td>US29</td>
      <td>Configure Pack Cooldown Interval</td>
      <td>Allows administrators to define or adjust the cooldown period between free pack openings.</td>
      <td>As an administrator, I want to configure the cooldown interval for free packs, so that I can control how frequently users obtain new cards.</td>
      <td>
        <ul>
          <li>Given an administrator sets a new cooldown interval, when the change is saved, then the system applies the new interval to future pack openings.</li>
          <li>Given an invalid interval is submitted (e.g., negative or zero), when the administrator attempts to save it, then the system rejects the change and shows a validation error.</li>
        </ul>
      </td>
      <td>EP03</td>
    </tr>
    <tr>
      <td>US30</td>
      <td>Sort Personal Collection</td>
      <td>Allows users to order their own card collection by different attributes.</td>
      <td>As a user, I want to sort my personal collection by brand, purchase price, or current value, so that I can review my cards more conveniently.</td>
      <td>
        <ul>
          <li>Given a user is viewing their collection, when they select a sorting attribute, then the system reorders the collection accordingly.</li>
          <li>Given no sorting attribute is selected, when the collection loads, then cards are displayed in the default order (e.g., most recently acquired first).</li>
        </ul>
      </td>
      <td>EP05</td>
    </tr>
    <tr>
      <td>US31</td>
      <td>Collection Storage Limit Warning</td>
      <td>Warns users when they are approaching their collection's storage capacity.</td>
      <td>As a user, I want to be warned when my collection is close to its storage limit, so that I can decide whether to sell cards or subscribe to a plan.</td>
      <td>
        <ul>
          <li>Given a user's collection reaches a defined threshold (e.g., 90% of capacity), when they access their collection, then the system displays a warning indicating the remaining available slots.</li>
          <li>Given a user's collection is below the threshold, when they access their collection, then no warning is shown.</li>
        </ul>
      </td>
      <td>EP05</td>
    </tr>
    <tr>
      <td>US32</td>
      <td>Compare Available Subscription Plans</td>
      <td>Allows users to view and compare the different subscription plans before choosing one.</td>
      <td>As a user, I want to compare the available subscription plans and their benefits, so that I can choose the one that best fits my needs.</td>
      <td>
        <ul>
          <li>Given subscription plans exist in the system, when a user opens the plans comparison view, then the system displays each plan's price, storage limit, and other benefits side by side.</li>
          <li>Given a user already has an active plan, when they view the comparison, then their current plan is clearly highlighted.</li>
        </ul>
      </td>
      <td>EP06</td>
    </tr>
    <tr>
      <td>US33</td>
      <td>Audit Role Changes</td>
      <td>Keeps a record of role assignment changes for accountability and traceability.</td>
      <td>As an administrator, I want role changes to be logged, so that I can audit who changed a user's role and when.</td>
      <td>
        <ul>
          <li>Given an administrator changes a user's role, when the change is saved, then the system records the previous role, new role, responsible administrator, and timestamp.</li>
          <li>Given an audit log entry exists, when an administrator with sufficient permissions views the audit history, then the system displays the full list of role change records.</li>
        </ul>
      </td>
      <td>EP07</td>
    </tr>
  </tbody>
</table>
  </tbody>
</table>


<br><br><br>

## **Domain Requirements**

<table>
  <thead>
    <tr>
      <th>Block</th>
      <th>Covers</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Users & Authentication</td>
      <td>Password requirements, email uniqueness, JWT token expiration, valid roles</td>
    </tr>
    <tr>
      <td>Card Catalog</td>
      <td>Who can create cards, rarity immutability, status rules (active/inactive), non-depreciation of value</td>
    </tr>
    <tr>
      <td>Pack Opening</td>
      <td>Cooldown interval, randomness, exclusion of inactive cards from the pool</td>
    </tr>
    <tr>
      <td>Marketplace / Transactions</td>
      <td>Conditions to list, conditions to purchase, concurrency handling, price calculation/updates</td>
    </tr>
    <tr>
      <td>Personal Collection</td>
      <td>Default storage limit, filtering/sorting, behavior when the limit is exceeded</td>
    </tr>
    <tr>
      <td>Subscriptions</td>
      <td>Available plans, cancellation behavior (immediate vs. end of period), behavior on expiration without renewal</td>
    </tr>
    <tr>
      <td>Roles & Permissions</td>
      <td>What each role can do, permission hierarchy, who can assign roles</td>
    </tr>
  </tbody>
</table>

### Block 1: User Management & Authentication

**RN-01 | Email Uniqueness**  
**Description:** Every registered email address must be unique within the system. No two user accounts may share the same email address.  
**Applies to:** EPIC-01, US01  
**Example / Exception:** If a user attempts to register using an email address that already exists, the system must reject the request and display a clear error message.

---

**RN-02 | Minimum Password Requirements**  
**Description:** Every password must satisfy the minimum security requirements defined by the system, including minimum length and character composition (uppercase letters, lowercase letters, numbers, and/or special characters). The exact requirements will be specified during the technical design phase.  
**Applies to:** EPIC-01, US01  
**Example / Exception:** None.

---

**RN-03 | JWT-Based Authentication**  
**Description:** Access to protected system resources requires a valid, non-expired JWT issued after a successful authentication.  
**Applies to:** EPIC-01, US02  
**Example / Exception:** Requests containing an invalid or expired JWT must be rejected, requiring the user to authenticate again.

---

**RN-04 | Token Expiration**  
**Description:** Every JWT has a predefined lifetime (TTL). Once the token expires, it can no longer be used to authenticate requests.  
**Applies to:** EPIC-01, US02  
**Example / Exception:** A refresh token mechanism may be evaluated in the future if required, but it is currently outside the project's scope.

---

**RN-05 | Session Invalidation on Logout**  
**Description:** After a user logs out, the current authenticated session must no longer be valid, preventing further access using the same authentication token.  
**Applies to:** EPIC-01, US22  
**Example / Exception:** None.

---

**RN-06 | Valid System Roles**  
**Description:** Every user must have exactly one valid role assigned within the system: **Administrator**, **Developer**, or **Regular User**. Users cannot exist without an assigned role.  
**Applies to:** EPIC-01, EPIC-07, US01, US17  
**Example / Exception:** Users who register through the application are assigned the **Regular User** role by default. **Administrator** and **Developer** roles may only be assigned manually by an authorized administrator.

---

**RN-07 | Deactivated Account Status**  
**Description:** A user account marked as **Inactive** cannot authenticate or perform any action within the system. The account and its historical data must remain stored for auditing and traceability purposes.  
**Applies to:** EPIC-01, US23  
**Example / Exception:** If a user with an inactive account attempts to log in using valid credentials, the authentication request must be rejected and an appropriate message must be displayed.


### Block 2: Card Catalog

**RN-08 | Exclusive Card Creation by Administrators**  
**Description:** Only users with the **Administrator** role are allowed to create new cards. Regular users cannot create cards under any circumstances.  
**Applies to:** EPIC-02, US04  
**Example / Exception:** None.

---

**RN-09 | Rarity Immutability**  
**Description:** Once a card's rarity is assigned during its creation, it cannot be modified afterward, even by an administrator.  
**Applies to:** EPIC-02, US04  
**Example / Exception:** None.

---

**RN-10 | Card Type Immutability**  
**Description:** A card's type or category is part of its identity and cannot be modified after the card has been created.  
**Applies to:** EPIC-02, US04  
**Example / Exception:** None.

---

**RN-11 | Permanent Base Value**  
**Description:** If a card has a base value defined by the system, that value remains constant throughout the card's lifetime and is not affected by marketplace activity or the passage of time.  
**Applies to:** EPIC-02, US04  
**Example / Exception:** This rule does not restrict the selling price defined by the card owner in the marketplace.

---

**RN-12 | Unique Card Ownership**  
**Description:** Every card can belong to only one user at any given time. Card ownership can only change through a valid marketplace transaction.  
**Applies to:** EPIC-04, US08  
**Example / Exception:** None.

---

**RN-13 | Soft Delete for Cards**  
**Description:** Cards are never permanently deleted from the database. When an administrator decides to remove a card from circulation, its status must be changed to **Inactive** instead.  
**Applies to:** EPIC-02, US05  
**Example / Exception:** None.

---

**RN-14 | Effects of Card Deactivation**  
**Description:** An **Inactive** card cannot be obtained through card packs, listed in the marketplace, or purchased by other users. However, it remains visible in its owner's collection and in historical records such as completed transactions.  
**Applies to:** EPIC-02, US05  
**Example / Exception:** None.

---

**RN-15 | Card Reactivation**  
**Description:** An administrator may change a card's status from **Inactive** to **Active**, making it available again for card packs and marketplace listings.  
**Applies to:** EPIC-02  
**Example / Exception:** None.

---

**RN-16 | Unique Card Distribution**  
**Description:** Each card can only be awarded once through the card pack system. Once a card has been assigned to a user, it cannot be obtained again through another pack. Ownership may only change through a valid marketplace transaction.  
**Applies to:** EPIC-03, US06, US08  
**Example / Exception:** None.

### Block 3: Pack Opening

**RN-17 | Pack Cooldown Interval**  
**Description:** A user may open only one free card pack during each configured cooldown interval. The cooldown interval is defined and managed by an administrator.  
**Applies to:** EPIC-03, US06, US29  
**Example / Exception:** None.

---

**RN-18 | Random Card Assignment**  
**Description:** Each free card pack must award exactly one randomly selected card from the pool of eligible active cards.  
**Applies to:** EPIC-03, US06  
**Example / Exception:** None.

---

**RN-19 | Exclusion of Inactive Cards from Pack Distribution**  
**Description:** Cards with an **Inactive** status must never be included in the pool of cards available for pack distribution.  
**Applies to:** EPIC-03, US06  
**Example / Exception:** None.

---

**RN-20 | Pack Cooldown Enforcement**  
**Description:** A user cannot open another free card pack until the configured cooldown interval has elapsed.  
**Applies to:** EPIC-03, US06, US13  
**Example / Exception:** If a user attempts to open a pack before the cooldown expires, the request must be rejected and the remaining waiting time must be displayed.

### Block 4: Marketplace / Transactions

**RN-21 | Ownership Required to List a Card**  
**Description:** Only the current owner of a card may publish it for sale in the marketplace.  
**Applies to:** EPIC-04, US07  
**Example / Exception:** None.

---

**RN-22 | Single Active Listing per Card**  
**Description:** A card may have only one active marketplace listing at any given time.  
**Applies to:** EPIC-04, US07  
**Example / Exception:** None.

---

**RN-23 | Free Price Setting**  
**Description:** The owner of a card is free to define its selling price when publishing it in the marketplace, provided it complies with the pricing rules established by the system.  
**Applies to:** EPIC-04, US07  
**Example / Exception:** The selling price must be greater than zero.

---

**RN-24 | Ownership Transfer After Purchase**  
**Description:** Once a purchase has been successfully completed, ownership of the card is transferred immediately and exclusively to the buyer. The card is automatically removed from the marketplace.  
**Applies to:** EPIC-04, US08  
**Example / Exception:** None.

---

**RN-25 | Concurrent Purchase Resolution**  
**Description:** A card can only be sold once per marketplace listing. If multiple users attempt to purchase the same card simultaneously, only one purchase may be completed successfully.  
**Applies to:** EPIC-04, US24  
**Example / Exception:** All unsuccessful purchase attempts must be rejected.

---

**RN-26 | Transaction History**  
**Description:** Every completed marketplace transaction must be permanently recorded, including the buyer, seller, card, sale price, and transaction date.  
**Applies to:** EPIC-04, US08, US11  
**Example / Exception:** None.

---

**RN-27 | Listing Cancellation**  
**Description:** The owner of an active marketplace listing may cancel it at any time before the card is purchased. Once cancelled, the card returns to the owner's collection and is no longer visible in the marketplace.  
**Applies to:** EPIC-04, US12  
**Example / Exception:** A completed sale cannot be cancelled.

---

**RN-28 | Marketplace Eligibility**  
**Description:** Only active cards that are currently owned by a user may be listed in the marketplace. Cards marked as **Inactive** cannot be published for sale.  
**Applies to:** EPIC-04, US07  
**Example / Exception:** None.

---

**RN-29 | Self-Purchase Restriction**  
**Description:** A user cannot purchase a card that they currently own.  
**Applies to:** EPIC-04, US08  
**Example / Exception:** None.

---

**RN-30 | Card Ownership During Listing**  
**Description:** A card listed in the marketplace remains the property of its current owner until the listing is cancelled or a purchase transaction is successfully completed.  
**Applies to:** EPIC-04, US07, US08, US12  
**Example / Exception:** None.

### Block 5: Personal Collection

**RN-31 | Default Storage Limit**  
**Description:** Every user without an active subscription has a predefined maximum number of cards that can be stored in their personal collection.  
**Applies to:** EPIC-05, EPIC-06, US10, US14  
**Example / Exception:** None.

---

**RN-32 | Storage Limit Enforcement**  
**Description:** A user whose personal collection has reached its storage limit cannot acquire additional cards until storage space becomes available or the storage limit is increased through an active subscription.  
**Applies to:** EPIC-05, EPIC-06, US06, US08, US14  
**Example / Exception:** None.

---

**RN-33 | Storage Capacity Warning**  
**Description:** The system must notify users when their personal collection reaches a predefined percentage of its maximum storage capacity.  
**Applies to:** EPIC-05, US31  
**Example / Exception:** The default notification threshold may be configured by an administrator (e.g., 90% of the available capacity).

---

**RN-34 | Subscription Storage Extension**  
**Description:** Activating a subscription plan increases the maximum number of cards that a user can store in their personal collection according to the limits defined by the selected plan.  
**Applies to:** EPIC-06, US14  
**Example / Exception:** If a subscription expires, the user's storage limit is recalculated according to the default limit or the limits defined by another active subscription.

---

**RN-35 | Card Acquisition Restriction**  
**Description:** A card cannot be assigned to a user whose personal collection has reached its maximum storage capacity. This restriction applies regardless of how the card is acquired (e.g., marketplace purchase or card pack opening).  
**Applies to:** EPIC-03, EPIC-05, EPIC-06, US06, US08, US14  
**Example / Exception:** The acquisition request must be rejected until sufficient storage space becomes available or the user's storage capacity is increased.

### Block 6: Subscriptions

**RN-36 | Subscription Storage Extension**  
**Description:** An active subscription increases the maximum number of cards that a user can store in their personal collection according to the limits defined by the selected subscription plan.  
**Applies to:** EPIC-06, US14  
**Example / Exception:** None.

---

**RN-37 | Single Active Subscription per User**  
**Description:** A user may have only one active subscription at any given time.  
**Applies to:** EPIC-06, US14  
**Example / Exception:** None.

---

**RN-38 | Subscription Validity Period**  
**Description:** Every subscription must have a creation date and an expiration date. A subscription is considered active only during its validity period.  
**Applies to:** EPIC-06, US14  
**Example / Exception:** None.

---

**RN-39 | Subscription Cancellation**  
**Description:** A user may cancel their active subscription at any time. Cancelling a subscription does not modify its expiration date, and the subscription benefits remain available until the subscription expires.  
**Applies to:** EPIC-06, US16  
**Example / Exception:** None.

---

**RN-40 | Storage Limit Reversion**  
**Description:** If, upon subscription expiration, a user's stored card count exceeds the allowed storage limit, no cards are removed from the collection. However, the user cannot acquire additional cards until the number of stored cards is within the allowed limit or a new subscription is activated.  
**Applies to:** EPIC-06, US16  
**Example / Exception:** None.
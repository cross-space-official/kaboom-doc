# Kaboom Service Architecture

## Overview

The kaboom-service is a Go-based microservice. It utilizes various libraries and frameworks to handle API requests, database operations, and blockchain interactions.

## Key Components

### 1. Main Application Entry Point

The main entry point of the application is responsible for setting up the core components of the service, including:

* Gin web framework for handling HTTP requests
* Database migration using golang-migrate
* Event bus initialization
* Service initialization for various components (Geth, User, Asset, Price, PriceFeed)
* Transaction synchronization (for primary pods only)
* Router setup

### 2. API Definition

The service's API is defined using OpenAPI (Swagger) specification. It outlines various endpoints for operations such as:

* Pair management
* User authentication
* Token operations
* Price data retrieval
* Social media integrations

### 3. Database

The service uses PostgreSQL as its primary database, with migrations handled by golang-migrate. Migration files are stored in a dedicated directory.

### 4. Service Layer

The service layer is composed of multiple services, each responsible for specific functionality:

* GethService: Handles interactions with Ethereum nodes
* UserService: Manages user-related operations
* AssetService: Handles asset-related functionality
* PriceService: Deals with price data
* PriceFeedService: Manages price feed operations

These services are initialized in the main function and injected into the handlers.

### 5. Repository Layer

The service uses a repository pattern for data access. Repositories are initialized for:

* EventLog
* Asset

### 6. Event Bus

An event bus is utilized for handling asynchronous operations.

### 7. Configuration

The service uses a configuration system, likely file-based, to manage various settings such as database connections, onchain client configurations, and server settings.

### 8. Containerization and Deployment

The service is containerized using Docker and deployment is managed through GitHub Actions workflows. These workflows handle building, testing, and deploying the service to different environments.

## Key Features

1. Blockchain Interaction: The service interacts with Ethereum-compatible blockchains, handling operations like balance checks, token transfers, and smart contract interactions.
2. User Management: Includes features for user registration, authentication, and wallet management.
3. Asset Management: Handles various operations related to cryptocurrency assets, including buying, selling, and transferring tokens.
4. Price Feeds: Integrates with price feed services to provide up-to-date cryptocurrency pricing information.
5. Multi-chain Support: The architecture suggests support for multiple blockchain networks, with configurations for different chain IDs.
6. Social Media Integration: Includes endpoints for social media authorization, potentially for user authentication or social sharing features.
7. Favorite Pairs: Functionality for users to mark and retrieve favorite trading pairs.
8. Search Functionality: Endpoints for searching through available trading pairs.

## Conclusion

The kaboom-service is a microservice architecture designed to handle various blockchain and cryptocurrency-related operations. It leverages Go's ecosystem, uses PostgreSQL for data persistence, and implements containerization for deployment. The service is structured with clear separation of concerns, utilizing repositories for data access, services for business logic, and handlers for API endpoints. Its modular design allows for easy expansion and maintenance of cryptocurrency-related features across multiple blockchain networks.
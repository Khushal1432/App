# CRED-style Financial Profile Application

## Overview

This is a modern web application built with React, Express, and Drizzle ORM. It provides a mobile-first user interface for financial profiles, displaying user information, credit scores, rewards, and transactions. The app follows a client-server architecture with a RESTful API backend and a React frontend styled using Tailwind CSS and shadcn/ui components.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

This application follows a typical React + Express architecture with some modern tooling:

1. **Frontend**: React application built with Vite, using Tailwind CSS and shadcn/ui for styling and components
2. **Backend**: Express.js server with RESTful API endpoints
3. **Database**: Drizzle ORM for database interactions (configured for PostgreSQL)
4. **Authentication**: Basic authentication system with username/password (schema defined but not fully implemented)
5. **State Management**: React Query for server state management

The application uses a monorepo structure, with client, server, and shared code organized in separate directories. This allows for code sharing between frontend and backend (e.g., database schemas, types).

## Key Components

### Frontend

1. **Component Library**: Extensive use of shadcn/ui components, which are built on top of Radix UI primitives. These provide accessible, customizable UI elements with a consistent design language.

2. **Pages**: 
   - Profile page: Displays user financial information, credit score, rewards, and transactions
   - 404 page: Simple error page for handling invalid routes

3. **API Integration**: Uses React Query for data fetching, caching, and state management of server data

4. **Styling**: Tailwind CSS with custom color scheme defined in tailwind.config.ts, giving a dark-themed UI

### Backend

1. **API Routes**: Express server with API endpoints for user data
   - `/api/profile`: Returns user profile information

2. **Storage**: 
   - Interface-based storage system allowing for multiple implementations
   - Currently using in-memory storage (`MemStorage`) with CRUD operations for user data
   - Schema defined for eventual PostgreSQL integration

3. **Development Tools**:
   - Vite integration for development with HMR (Hot Module Replacement)
   - Logging middleware for API requests

## Data Flow

1. **Client Requests**: 
   - React components make requests to backend API endpoints using React Query
   - The queries are defined with proper caching and error handling

2. **Server Processing**:
   - Express server receives requests and routes them to appropriate handlers
   - Routes execute business logic and interact with storage
   - Server sends JSON responses back to client

3. **Data Display**:
   - React components receive data and render the UI
   - UI components are organized into logical sections (ProfileHeader, FinancialInfo, etc.)

## External Dependencies

### Frontend

1. **UI Components**: 
   - @radix-ui/* packages for accessible UI primitives
   - shadcn/ui components built on top of Radix UI

2. **Data Management**:
   - @tanstack/react-query for server state management

3. **Routing**:
   - wouter for lightweight client-side routing

### Backend

1. **Database**:
   - drizzle-orm for database ORM
   - @neondatabase/serverless for PostgreSQL connectivity (currently not actively used)

2. **Validation**:
   - zod for schema validation and type generation

## Deployment Strategy

The application is configured for deployment on Replit:

1. **Development**: `npm run dev` starts both the backend server and frontend dev server with HMR

2. **Build**: 
   - `npm run build` builds the React app with Vite and bundles the server with esbuild
   - Frontend assets are output to dist/public
   - Server is bundled to dist/index.js

3. **Production**:
   - `npm run start` runs the production build
   - Static files are served by Express
   - Environment variables differentiate between development and production

4. **Database**:
   - PostgreSQL is configured as a module in the Replit environment
   - Drizzle ORM is set up to connect to the database (requires DATABASE_URL environment variable)

## Future Development Considerations

1. **Database Integration**: 
   - Currently using in-memory storage, but schema is ready for PostgreSQL
   - Need to implement the PostgreSQL storage adapter

2. **Authentication**: 
   - User schema exists but authentication flow needs to be implemented
   - Session management should be added

3. **Additional Features**:
   - Transaction history needs to be implemented
   - Vehicle and financial data needs real API integrations

4. **Testing**: 
   - No tests are currently implemented
   - Should add unit and integration tests
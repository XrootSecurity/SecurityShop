# Overview

This is a full-stack web application for a cybersecurity tools marketplace built with React frontend and Node.js/Express backend. The application features a hacker/cyberpunk theme with a green matrix-style design. Users can browse security tools, make purchases through a DANA payment system, and administrators can manage products and orders.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

The application follows a monorepo structure with clear separation between client, server, and shared code:

- **Frontend**: React with TypeScript, using Vite for development and building
- **Backend**: Express.js server with TypeScript
- **Database**: PostgreSQL with Drizzle ORM for type-safe database operations
- **UI Framework**: Shadcn/UI components with Radix UI primitives and Tailwind CSS
- **State Management**: TanStack Query for server state management
- **Routing**: Wouter for client-side routing
- **File Storage**: Local file system with multer for uploads

## Key Components

### Frontend Architecture
- **Component Library**: Shadcn/UI with custom cyberpunk styling
- **Styling**: Tailwind CSS with custom CSS variables for theming
- **State Management**: React Query for server state, local React state for UI
- **Navigation**: Wouter-based routing with shop and admin pages
- **Device Identification**: Custom device fingerprinting for user sessions

### Backend Architecture
- **API Design**: RESTful endpoints with Express.js
- **Database Layer**: Drizzle ORM with PostgreSQL dialect
- **Storage Interface**: Abstracted storage layer (currently in-memory, designed for database migration)
- **File Handling**: Multer middleware for image and file uploads
- **Authentication**: Simple credential-based admin authentication

### Database Schema
- **Products**: Store security tools with images, files, and metadata
- **Orders**: Track customer purchases with device-based identification
- **User Sessions**: Maintain user state across sessions using device fingerprinting

## Data Flow

1. **Product Browsing**: Users view products fetched from the backend storage
2. **Cart Management**: Client-side cart state with localStorage persistence
3. **Order Creation**: Orders submitted with device ID for user tracking
4. **Payment Flow**: DANA QRIS payment with proof upload functionality
5. **Admin Management**: Separate admin interface for order approval and product management

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: Database connection (Neon PostgreSQL)
- **drizzle-orm**: Type-safe database operations
- **@tanstack/react-query**: Server state management
- **@radix-ui/***: Headless UI components
- **tailwindcss**: Utility-first CSS framework
- **multer**: File upload handling
- **wouter**: Lightweight React router

### Development Tools
- **Vite**: Fast development server and build tool
- **TypeScript**: Type safety across the stack
- **ESBuild**: Fast JavaScript bundler for production

## Deployment Strategy

The application is configured for Replit deployment with:

- **Development**: `npm run dev` starts both frontend and backend in development mode
- **Build**: `npm run build` creates optimized production builds
- **Production**: `npm start` serves the built application
- **Database**: Drizzle migrations with `npm run db:push`

The Vite configuration includes Replit-specific plugins for development debugging and error overlays. The application serves static files in production and uses Vite's development server in development mode.

### Environment Configuration
- Database connection via `DATABASE_URL` environment variable
- Development/production mode detection via `NODE_ENV`
- Replit-specific features enabled via `REPL_ID` detection
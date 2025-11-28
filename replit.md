# SkillForge: AI-Driven Adaptive Learning Platform

## Overview

SkillForge is an AI-powered adaptive learning and exam generation platform designed for educational technology. The application serves multiple user roles (students, guardians, instructors, and administrators) with personalized learning experiences, progress tracking, and intelligent assessment generation.

The platform is built as a full-stack web application with a React-based frontend and Express backend, featuring role-based dashboards, course management, and analytics capabilities.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework & Routing**: React 18+ with Wouter for client-side routing, using functional components and hooks throughout.

**State Management**: Context API is used for authentication state management via `AuthContext`, which handles user authentication, role selection, and session persistence through localStorage.

**UI Component System**: The application uses shadcn/ui components built on Radix UI primitives with a customized Material Design-inspired theme. Components follow a glass morphism design pattern with semi-transparent backgrounds, subtle shadows, and gradient accents.

**Design System**:
- Typography: Inter font family with defined weight scales (400 for body, 500 for medium, 600-700 for headers)
- Spacing: Tailwind utility classes with consistent 2, 4, 6, 8, 12, 16 unit scale
- Color Scheme: HSL-based color system with CSS custom properties for theming, featuring a violet/purple primary gradient
- Responsive Layout: Mobile-first approach with breakpoint-specific grid systems (3-column desktop, 2-column tablet, single-column mobile)

**Component Architecture**:
- Custom glass-effect cards (`GlassCard`, `StatCard`, `ActionCard`) for visual consistency
- Reusable `Topbar` component with dynamic title, back navigation, and user actions
- `ProgressBar` component for tracking learning completion
- Protected route wrappers for role-based access control

### Backend Architecture

**Server Framework**: Express.js with TypeScript running on Node.js, using ES modules.

**API Structure**: RESTful API design with routes prefixed under `/api`. The routing system is modularized through `registerRoutes` function in `server/routes.ts`.

**Storage Layer**: Abstracted storage interface (`IStorage`) with initial in-memory implementation (`MemStorage`). The interface defines CRUD operations for user management and can be extended for additional entities.

**Development Setup**: Vite middleware integration for hot module replacement during development, with separate production build pipeline using esbuild for server bundling.

**Session Management**: Prepared for session handling with connect-pg-simple for PostgreSQL-based sessions (infrastructure in place via dependencies).

### Data Storage

**Database**: PostgreSQL via Neon serverless driver (`@neondatabase/serverless`).

**ORM**: Drizzle ORM for type-safe database operations with schema-first design approach.

**Schema Structure**: Currently defines a `users` table with UUID primary keys, username (unique), and password fields. The schema uses Drizzle's PostgreSQL dialect and integrates with Zod for runtime validation via `drizzle-zod`.

**Migrations**: Configured to output migration files to `./migrations` directory with schema definition in `shared/schema.ts`.

### Authentication & Authorization

**Role-Based Access**: Four distinct user roles (student, guardian, instructor, admin) with separate dashboard routes and protected route components.

**Session Persistence**: LocalStorage-based session management storing selected role (`sf_selected_role`) and user name (`sf_user_name`).

**Route Protection**: `ProtectedRoute` component wrapper validates authentication status and role-based access, redirecting unauthorized users appropriately.

### Build & Deployment

**Build Pipeline**: 
- Client: Vite builds React application to `dist/public`
- Server: esbuild bundles server code with selective dependency bundling (allowlist approach for frequently-used packages to reduce syscalls)
- Production: Single CommonJS output (`dist/index.cjs`) serving both API and static files

**Development Workflow**: 
- Dev mode: Vite dev server with HMR at `/vite-hmr`
- Replit-specific plugins: Cartographer for code mapping and dev banner integration
- TypeScript compilation checking via `tsc --noEmit`

**Static File Serving**: Express serves Vite-built static files from `dist/public` with fallback to `index.html` for SPA routing.

## External Dependencies

### UI & Styling
- **Tailwind CSS**: Utility-first CSS framework with custom configuration for design system
- **Radix UI**: Headless component primitives for accessible UI components
- **shadcn/ui**: Pre-built component library following New York style variant
- **Lucide React**: Icon library for consistent iconography
- **class-variance-authority**: For component variant management

### Data & State Management
- **@tanstack/react-query**: Server state management with caching and synchronization
- **React Hook Form**: Form state management with `@hookform/resolvers` for validation
- **Zod**: Schema validation for forms and API data

### Backend Infrastructure
- **Drizzle ORM**: Type-safe ORM with `drizzle-zod` integration for schema validation
- **@neondatabase/serverless**: Serverless PostgreSQL driver for Neon database
- **express-session**: Session middleware with `connect-pg-simple` for PostgreSQL session storage
- **Passport.js**: Authentication middleware (prepared via `passport` and `passport-local` dependencies)

### Development Tools
- **Vite**: Build tool and dev server with React plugin
- **esbuild**: Fast JavaScript bundler for production builds
- **TypeScript**: Type safety across full stack with path aliases configured

### Third-Party Services (Prepared)
The dependency list indicates preparation for:
- **Stripe**: Payment processing
- **OpenAI/Google Generative AI**: AI-powered features for adaptive learning and exam generation
- **Nodemailer**: Email notifications
- **WebSocket (ws)**: Real-time communication capabilities
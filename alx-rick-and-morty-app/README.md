# 🚀 Rick and Morty Episodes App with Error Boundary

A modern Next.js application that demonstrates React Error Boundaries implementation while showcasing episodes from the Rick and Morty universe. This project is part of the ALX GraphQL curriculum, focusing on error handling, monitoring, and graceful failure recovery in React applications.

![Next.js](https://img.shields.io/badge/Next.js-14-black?style=for-the-badge&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Sentry](https://img.shields.io/badge/Sentry-362D59?style=for-the-badge&logo=sentry&logoColor=white)

## 🌟 Project Overview

This application serves as a comprehensive demonstration of error handling patterns in modern React applications. It implements React Error Boundaries to gracefully handle JavaScript errors that occur during component rendering, providing users with meaningful feedback and recovery options.

### Learning Objectives Achieved

- ✅ **Error Boundary Implementation**: Created a robust class component to catch and handle errors
- ✅ **Component Lifecycle**: Utilized `getDerivedStateFromError` and `componentDidCatch` methods
- ✅ **Error Recovery**: Implemented user-friendly "Try again" functionality
- ✅ **Error Monitoring**: Integrated Sentry for production error tracking and analytics
- ✅ **TypeScript Integration**: Full type safety with proper interfaces and error handling
- ✅ **Testing Strategy**: Created intentional error scenarios for boundary validation

## 🚀 Features

### Core Functionality
- **Episode Gallery**: Browse through all Rick and Morty episodes
- **Real-time Data**: Fetches data from the official Rick and Morty GraphQL API
- **Responsive Design**: Works seamlessly on desktop and mobile devices
- **Pagination**: Navigate through episodes with Previous/Next controls
- **TypeScript**: Full type safety throughout the application

### Error Handling Features
- **Error Boundary**: Graceful error handling with fallback UI
- **Error Recovery**: Users can reset error state without page reload
- **Error Monitoring**: Integrated with Sentry for production error tracking
- **Component Isolation**: Prevents single component failures from crashing entire app
- **Detailed Logging**: Comprehensive error information for debugging

## 🛠️ Tech Stack

| Category | Technology | Purpose |
|----------|------------|---------|
| **Framework** | Next.js 15 | React framework with SSR/SSG capabilities |
| **Language** | TypeScript | Type safety and developer experience |
| **Error Monitoring** | Sentry | Production error tracking and analytics |
| **Error Handling** | React Error Boundaries | Graceful error recovery |
| **GraphQL Client** | Apollo Client | Data fetching and caching |
| **Styling** | Tailwind CSS | Utility-first CSS framework |
| **API** | Rick and Morty GraphQL API | Episode data source |

## 📁 Project Structure

```
alx-rick-and-morty-app/
├── components/
│   ├── ErrorBoundary.tsx        # Error boundary component
│   ├── ErrorProneComponent.tsx  # Test component for error boundary
│   └── common/
│       └── EpisodeCard.tsx      # Individual episode card component
├── graphql/
│   └── queries.ts               # GraphQL queries
├── interfaces/
│   └── index.ts                 # TypeScript type definitions
├── pages/
│   ├── _app.tsx                 # App wrapper with Error Boundary
│   └── index.tsx                # Main page component
├── styles/
│   └── globals.css              # Global styles with Tailwind
├── sentry.client.config.js      # Sentry client configuration
├── sentry.server.config.js      # Sentry server configuration
├── .env.local                   # Environment variables (Sentry DSN)
├── package.json                 # Dependencies and scripts
├── tsconfig.json                # TypeScript configuration
└── next.config.js               # Next.js configuration
```

## 🛡️ Error Boundary Implementation

### Overview
This project implements a comprehensive error handling solution using React Error Boundaries to gracefully handle JavaScript errors that occur during rendering, preventing complete application crashes and providing users with meaningful feedback.

### Key Components

#### 🔧 ErrorBoundary Class Component
- **Location**: `components/ErrorBoundary.tsx`
- **Type**: React Class Component with TypeScript interfaces
- **Features**:
  - Catches JavaScript errors in child component tree
  - Provides fallback UI with "Try again" functionality
  - Logs errors to console and Sentry for monitoring
  - Implements proper lifecycle methods (`getDerivedStateFromError`, `componentDidCatch`)

```typescript
interface State {
  hasError: boolean;
}

interface ErrorBoundaryProps {
  children: ReactNode;
}

class ErrorBoundary extends React.Component<ErrorBoundaryProps, State> {
  // Implementation details...
}
```

#### 🔄 Error Recovery Mechanism
- **User Experience**: Users can click "Try again?" to reset error state
- **State Management**: Component state resets without page reload
- **Application Continuity**: App continues functioning even after component failures
- **Crash Prevention**: Prevents entire application crashes from single component errors

#### 📊 Error Monitoring with Sentry
- **Integration**: `@sentry/react` and `@sentry/nextjs` packages
- **Features**:
  - Automatic error capture and reporting to Sentry dashboard
  - Component stack traces for debugging
  - Production error monitoring and analytics
  - Real-time error notifications and alerts
  - Error grouping and frequency tracking

### Implementation Architecture

```typescript
// Application wrapper with Error Boundary
function MyApp({ Component, pageProps }: AppProps) {
  return (
    <ErrorBoundary>
      <Component {...pageProps} />
    </ErrorBoundary>
  );
}
```

### 🧪 Testing Error Handling

The project includes comprehensive error testing:

#### ErrorProneComponent
- **Purpose**: Intentionally throws errors for testing error boundary functionality
- **Location**: `components/ErrorProneComponent.tsx`
- **Features**: Demonstrates error boundary activation and fallback UI

#### Test Scenarios
1. **Component Rendering Errors**: Simulated with ErrorProneComponent
2. **Runtime JavaScript Errors**: Caught and handled gracefully
3. **Error Recovery Testing**: "Try again" functionality validation
4. **Sentry Integration Testing**: Error reporting to monitoring dashboard

### Production Benefits
- **User Experience**: Graceful degradation instead of white screens
- **Error Tracking**: Comprehensive error monitoring and analytics
- **Debugging**: Detailed error information for quick resolution
- **Reliability**: Application stability and improved uptime
- **User Retention**: Users can recover from errors without leaving the app

## 🏃‍♂️ Quick Start Guide

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn

### Installation & Setup

1. **Navigate to the project directory**:
   ```bash
   cd alx-rick-and-morty-app
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Configure Sentry (Optional)**:
   - Create a Sentry account at [sentry.io](https://sentry.io)
   - Create a new project and get your DSN
   - Add your Sentry DSN to `.env.local`:
     ```
     NEXT_PUBLIC_SENTRY_DSN=https://your-dsn@sentry.io/project-id
     SENTRY_DSN=https://your-dsn@sentry.io/project-id
     ```

4. **Start the development server**:
   ```bash
   npm run dev
   ```

5. **Open your browser**:
   Navigate to [http://localhost:3000](http://localhost:3000)

## 📋 Available Scripts

```bash
npm run dev      # Start development server
npm run build    # Build for production
npm run start    # Start production server
npm run lint     # Run ESLint
```

## 🔍 GraphQL Query

The app uses this GraphQL query to fetch episode data:

```graphql
query GetEpisodes($page: Int) {
  episodes(page: $page) {
    info {
      count
      pages
      next
      prev
    }
    results {
      id
      name
      air_date
      episode
    }
  }
}
```

## 🧩 Components

### EpisodeCard
- **Purpose**: Displays individual episode information
- **Props**: `id`, `name`, `air_date`, `episode`
- **Features**: Hover effects, responsive design, episode number badge

### Home Page
- **Features**: 
  - Episode grid layout
  - Loading and error states
  - Pagination controls
  - Responsive header and footer

## 📝 TypeScript Interfaces

```typescript
interface InfoProps {
  pages: number
  next: number
  prev: number
  count: number
}

interface EpisodeProps {
  id: number
  name: string
  air_date: string
  episode: string
  info: InfoProps
}

type EpisodeCardProps = Pick<EpisodeProps, 'id' | 'name' | 'air_date' | 'episode'>
```

## 🎨 Styling

- **Framework**: Tailwind CSS
- **Design System**: 
  - Primary colors: Blue-green gradient (`#A3D5E0` to `#F4F4F4`)
  - Accent colors: `#4CA1AF`, `#45B69C`
  - Cards: White background with shadow effects
  - Responsive grid system (1-4 columns based on screen size)

## 🔗 API Integration

- **Endpoint**: `https://rickandmortyapi.com/graphql`
- **Client**: Apollo Client with InMemoryCache
- **Features**: Automatic caching, loading states, error handling

## 🌟 Key Features Explained

### Pagination
- Uses React state to track current page
- Fetches new data when page changes
- Buttons disabled at boundaries (first/last page)

### Responsive Design
- Grid adapts from 1 column (mobile) to 4 columns (desktop)
- Cards scale and have hover effects
- Typography adjusts for different screen sizes

### Type Safety
- All data structures defined with TypeScript interfaces
- Props validation for components
- GraphQL response typing

## 🚦 Development Workflow

1. **Start development server**: `npm run dev`
2. **Make changes** to components or pages
3. **Hot reload** automatically updates the browser
4. **Build for production**: `npm run build`
5. **Test production build**: `npm run start`

## 📱 Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## 🤝 Contributing

We welcome contributions to improve this Error Boundary implementation! Here's how you can contribute:

### Development Setup
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Make your changes and test thoroughly
4. Ensure all TypeScript types are properly defined
5. Test error boundary functionality
6. Submit a pull request with detailed description

### Contribution Guidelines
- Follow TypeScript best practices
- Add proper error handling for new components
- Include tests for error scenarios
- Update documentation for new features
- Maintain consistent code style

## 🐛 Troubleshooting

### Common Issues

#### Sentry Integration
**Problem**: Sentry errors not appearing in dashboard
**Solution**: 
1. Verify DSN is correctly set in `.env.local`
2. Check Sentry project configuration
3. Ensure proper network connectivity

#### Error Boundary Not Catching Errors
**Problem**: Errors not being caught by Error Boundary
**Solution**:
1. Ensure errors occur in child components during rendering
2. Event handlers need separate try-catch blocks
3. Async errors require additional handling

#### TypeScript Compilation Errors
**Problem**: Type errors in Error Boundary implementation
**Solution**:
1. Ensure proper interface definitions
2. Check React and TypeScript version compatibility
3. Verify proper import statements

### Debug Mode
Enable debug logging by setting environment variable:
```bash
NEXT_PUBLIC_DEBUG=true
```

## 📊 Performance Considerations

### Error Boundary Impact
- **Minimal Performance Cost**: Error boundaries only activate during errors
- **Memory Usage**: Lightweight component state management
- **Bundle Size**: Sentry adds ~50KB to bundle (gzipped)

### Optimization Tips
- Use Error Boundaries strategically at component tree levels
- Avoid wrapping every component individually
- Implement proper error logging throttling in production
- Consider lazy loading for non-critical error monitoring features

## � Security Considerations

### Error Information
- Avoid logging sensitive data in error messages
- Sanitize user input before error reporting
- Use environment variables for sensitive configuration

### Sentry Configuration
- Restrict DSN access in production environments
- Configure proper data scrubbing rules
- Set appropriate retention policies

## 📈 Monitoring and Analytics

### Error Metrics to Track
- Error frequency and patterns
- Component failure rates
- User recovery success rates
- Error resolution times

### Sentry Dashboard Features
- Real-time error tracking
- Error grouping and classification
- Performance impact analysis
- User impact assessment

## 🚀 Deployment

### Production Checklist
- [ ] Configure Sentry DSN for production environment
- [ ] Set appropriate error sampling rates
- [ ] Test Error Boundary functionality in production build
- [ ] Verify error monitoring alerts are configured
- [ ] Review and test fallback UI in production environment

### Environment Variables
```bash
# Production
SENTRY_DSN=your-production-dsn
NEXT_PUBLIC_SENTRY_DSN=your-public-dsn

# Development
NEXT_PUBLIC_DEBUG=true
```

## �📄 License

This project is developed for educational purposes as part of the **ALX Software Engineering Program** - GraphQL specialization track. 

### Educational Use
- Free to use for learning and educational purposes
- Part of ALX curriculum requirements
- Demonstrates industry-standard error handling practices


### Learning Resources
- [React Error Boundaries Documentation](https://reactjs.org/docs/error-boundaries.html)
- [Sentry React Integration Guide](https://docs.sentry.io/platforms/javascript/guides/react/)
- [Next.js Error Handling](https://nextjs.org/docs/advanced-features/error-handling)
- [TypeScript Error Handling Patterns](https://www.typescriptlang.org/docs/handbook/2/narrowing.html)



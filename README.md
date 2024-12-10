# How to run:
Note: You need NPM in order to run this app.

1. npm install
2. npm run dev

# Objective:
Build a TypeScript-based React frontend application for a bookstore system.


All the task goals are reached:

1. The project is up on GitHub with regular commits.
2. The app works, even if not all features are done.
3. The README file contains the structure, tech choices, and what's missing.

That being said, I didn’t write a lot of code, and here’s why:

Before jumping into coding, you need to understand the business logic and ask questions. It’s all about building the right solution, not rushing through it. If you just want a code monkey who uses ChatGPT to quickly throw something together, I’m not the right fit.
Planning and setting things up properly came first.


# 1 A short description of the structure/architecture of the application.
```
src/
  ├── assets/                     # Static assets (images, fonts, etc.)
  ├── modules/                    # Feature-based organization
  │   ├── core/                   # Core functionality (Auth, Navigation, Notifications, etc.)
  │   │   ├── components/         # Reusable UI elements
  │   │   ├── design-system/      # Design system components
  │   │   ├── hooks/              # Shared custom hooks
  │   │   ├── lib/                # Reusable logic
  │   │   └── utils/              # General utility functions
  │   ├── books/                  # Books-related logic
  │   │   ├── components/         # Book list, card, search
  │   │   ├── hooks/              # Custom hooks for books
  │   │   ├── services/           # Book-related API calls
  │   │   ├── states/             # Local state for books
  │   │   └── utils/              # Book-specific helpers
  │   ├── cart/                   # Shopping cart logic
  │   │   ├── components/         # Cart sidebar, items
  │   │   ├── hooks/              # Cart management
  │   │   ├── services/           # Cart submission, checkout
  │   │   ├── states/             # Cart state (items, total)
  │   │   └── utils/              # Cart utilities
  │   ├── profile/                # User profile logic
  │   │   ├── components/         # Profile form, avatar
  │   │   ├── hooks/              # Profile management
  │   │   ├── services/           # Profile-related API calls
  │   │   ├── states/             # Profile state
  │   │   └── utils/              # Profile helpers
  ├── api/                        # Server communication (REST or GraphQL)
  ├── graphql/                    # GraphQL-related code
  ├── routes/                     # Routing logic (React Router)
  ├── pages/                      # Page-level components
  ├── states/                     # Global state management (e.g., Redux)
  ├── styles/                     # Global and component-level styles
  ├── types/                      # TypeScript types, enums, interfaces
  ├── configs/                    # App configurations
  ├── constants/                  # Constant values
  └── tests/                      # Unit and integration tests
```

# 2 Tech stack & key technical choices
Apart from the standard React with TypeScript I would choose Vite for fast builds, and React Router for navigation. I would use an internal library wrapped around Material UI with a custom theme for a quick and comprehensive UI.
Regarding data fetching, I would go with GraphQL due to better data fetching performance. Redux would handle global state like the cart functionality.
Tests would use Vitest because its fast fast, and Playwright for end-to-end testing.
AWS for backend services and GitHub Actions for easy CI/CD.
I would track users with Amplitude and monitor errors with Sentry.

# 3 Summary of features that were not implemented
1. Search feature:
I would put the logic on the backend for better performance. Doing it on the frontend would be slower and less scalable.

2. List of books:
I would use a virtualized list to load only a small batch (50/100 books) at a time. Then add pagination or infinite scroll to load more as needed to keep it fast.

3. Stock quantity & cart management:
I would use GraphQL subscriptions to keep it updated in real-time. This would prevent users from getting frustrated by an "out of stock" due to high traffic.

4. User profile:
I would fetch the latest data when the user hits the edit profile functionality to ensure the data is up-to-date with the server.
Also, I would add a timestamp to the request to prevent race conditions and ensure that updates are applied in the correct order, especially if multiple updates are happening at once.

# Saas Application files organization

root
├── app
│   ├── layout.tsx                 // Root layout (Html/Body tags)
│   ├── globals.css                // Global styles
│   │
│   ├── (marketing)                // Route Group: Public pages (URL doesn't show /marketing)
│   │   ├── layout.tsx             // Marketing specific layout (e.g., transparent nav)
│   │   ├── page.tsx               // Landing page
│   │   └── _components            // Components ONLY used in marketing
│   │       ├── hero.tsx
│   │       └── pricing.tsx
│   │
│   ├── (platform)                 // Route Group: Authenticated app pages
│   │   ├── layout.tsx             // Dashboard layout (Sidebar + Topbar)
│   │   │
│   │   ├── dashboard              // URL: /dashboard
│   │   │   └── page.tsx
│   │   │
│   │   └── projects               // URL: /projects
│   │       ├── [projectId]        // Dynamic Route: /projects/123
│   │       │   ├── page.tsx
│   │       │   └── _components    // Components ONLY used in a single project view
│   │       │       ├── kanban-board.tsx
│   │       │       ├── task-card.tsx
│   │       │       └── project-settings.tsx
│   │       │
│   │       └── page.tsx           // List of all projects
│   │
│   └── api                        // Backend API routes
│       └── webhooks
│           └── stripe             // Route: /api/webhooks/stripe
│               └── route.ts
│
├── components                     // SHARED components used across multiple features
│   ├── ui                         // "Dumb" UI primitives (Buttons, Inputs, Modals)
│   │   ├── button.tsx
│   │   └── dialog.tsx
│   └── form-error.tsx             // A component used in both Marketing and Dashboard
│
├── lib                            // Utility functions (logic only, no UI)
│   ├── db.ts                      // Database connection
│   └── utils.ts                   // Helper functions (cn, formatters)
│
├── hooks                          // Reusable React hooks
│   └── use-mobile-sidebar.ts      // UI logic hook
│
└── middleware.ts                  // Edge middleware (Auth protection)

When and Where is this Used?
When to use it:

Medium-to-Large Applications: It prevents the "scrolling fatigue" of finding a specific file in a giant components folder.


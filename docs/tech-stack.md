---
description: An exhaustive breakdown of frameworks, styling tools, state systems, and libraries used across ACR applications.
---

# Technology Stack Documentation

This document outlines the core technical stack leveraged across the **ACR** ecosystem. Every technology is chosen based on performance, developer experience, type safety, and ecosystem stability.

---

## 🎨 Frontend Stack Overview

| Category | Primary Choice | Alternative / Contextual |
| :--- | :--- | :--- |
| **Framework** | **Next.js (App Router)** | React 19 (Vite), Vue 3 / Nuxt |
| **Language** | **TypeScript (Strict Mode)** | JavaScript ESNext |
| **Styling** | **Tailwind CSS v3/v4** | Vanilla CSS, CSS Modules |
| **Animation & Motion** | **Framer Motion** | GSAP, Canvas API |
| **3D & Creative** | **Three.js / React Three Fiber** | Drei, GLSL Shaders |
| **State Management** | **Zustand** (Client), **TanStack Query** (Server) | React Context |
| **Component Primitives** | **Radix UI Primitives** | Headless UI |
| **Icons & Media** | **Lucide Icons** | SVG Custom Sprites |
| **Validation** | **Zod** | Valibot |

---

## ⚡ Framework & Language

### 1. Next.js (App Router)

#### Why It Is Used
Next.js provides hybrid rendering capabilities (React Server Components, Static Site Generation, Incremental Static Regeneration, and Server-Side Rendering) with zero boilerplate. It allows optimal performance by sending static HTML and zero JavaScript for non-interactive content.

#### Implementation & Architecture
* **Directory Layout:** `app/` folder routing using route groups `(marketing)`, `(dashboard)`.
* **Server-First Strategy:** All components default to Server Components (`RSC`). Add `'use client'` only at leaf nodes that handle user interactions (events, hooks, motion).
* **Data Fetching:** Direct async/await inside Server Components with native `fetch` caching and tag revalidation.

#### Best Practices
* Keep client bundles lean by never importing heavy server packages into client boundaries.
* Colocate loading skeletons (`loading.tsx`) and localized error boundaries (`error.tsx`) with page routes.

```tsx
// app/showcase/page.tsx - React Server Component Example
import { Suspense } from 'react';
import ProjectGrid from '@/components/projects/ProjectGrid';
import ProjectSkeleton from '@/components/projects/ProjectSkeleton';

export const metadata = {
  title: 'Showcase | ACR Engineering',
  description: 'Interactive digital experiments and client platforms.',
};

export default async function ShowcasePage() {
  return (
    <main className="min-h-screen px-6 py-12 max-w-7xl mx-auto">
      <header className="mb-10">
        <h1 className="text-4xl font-extrabold tracking-tight text-white">
          Engineered Showcase
        </h1>
        <p className="mt-2 text-zinc-400">
          Selected high-performance web applications and design systems.
        </p>
      </header>
      
      <Suspense fallback={<ProjectSkeleton />}>
        <ProjectGrid />
      </Suspense>
    </main>
  );
}
```

---

### 2. TypeScript

#### Why It Is Used
TypeScript provides deterministic typing, autocompletion, compile-time error catching, and frictionless refactoring across growing codebases.

#### Best Practices
* Enable strict mode (`strict: true`, `noImplicitAny: true`, `exactOptionalPropertyTypes: true`).
* Enforce explicit interface boundaries for props, API responses, and database entities.
* Avoid `any` without compromise; use `unknown` with type narrowing or type guards.

```typescript
// types/project.ts - Strict Domain Type Definitions
export type ProjectCategory = 'creative-web' | 'enterprise-dashboard' | 'ai-interface';

export interface ProjectMetadata {
  id: string;
  slug: string;
  title: string;
  tagline: string;
  category: ProjectCategory;
  stars?: number;
  liveUrl?: string;
  githubUrl: string;
  technologies: readonly string[];
  metrics: {
    lighthouseScore: number;
    bundleSizeKb: number;
  };
}
```

---

## 💅 Styling & Visual Architecture

### 1. Tailwind CSS

#### Why It Is Used
Tailwind CSS provides rapid, utility-first styling with zero dead CSS in production. It guarantees consistency by enforcing design token constraints.

#### Best Practices
* Define design tokens (colors, font families, glow effects, glassmorphic filters) inside `tailwind.config.ts`.
* Use `clsx` and `tailwind-merge` via a standard `cn()` utility to prevent conflicting utility clashes in reusable components.

```typescript
// lib/utils.ts - Classname merger utility
import { clsx, type ClassValue } from 'clsx';
import { twMerge } from 'tailwind-merge';

export function cn(...inputs: ClassValue[]): string {
  return twMerge(clsx(inputs));
}
```

---

### 2. Framer Motion

#### Why It Is Used
Framer Motion is the gold standard for physics-based spring animations, layout transitions, gesture tracking, and scroll-linked animations in React.

#### Best Practices
* Use `AnimatePresence` for unmounting transitions.
* Leverage `motion` components with spring configurations (`damping`, `stiffness`) for organic feel rather than mechanical linear transitions.

```tsx
// components/ui/FadeIn.tsx
'use client';

import { motion } from 'framer-motion';
import { ReactNode } from 'react';

interface FadeInProps {
  children: ReactNode;
  delay?: number;
}

export default function FadeIn({ children, delay = 0 }: FadeInProps) {
  return (
    <motion.div
      initial={{ opacity: 0, y: 16 }}
      animate={{ opacity: 1, y: 0 }}
      exit={{ opacity: 0, y: -16 }}
      transition={{ duration: 0.4, delay, ease: [0.25, 0.4, 0.25, 1] }}
    >
      {children}
    </motion.div>
  );
}
```

---

### 3. Three.js / React Three Fiber (Creative Web)

#### Why It Is Used
Used for interactive 3D hero scenes, procedural background shaders, interactive particles, and spatial canvas presentations.

#### Best Practices
* Dispose geometries and materials on component unmount to prevent WebGL memory leaks.
* Run heavy calculation loops inside `useFrame` utilizing delta time.

---

## 🗄️ State Management Architecture

### Client State: Zustand
* Lightweight (<1kB), zero boilerplate, and free of React Context re-render cascades.
* Used for modal states, UI preferences, theme toggling, and interactive canvas tools.

```typescript
// store/useUIStore.ts
import { create } from 'zustand';

interface UIState {
  sidebarOpen: boolean;
  activeFilter: string;
  setSidebarOpen: (open: boolean) => void;
  setActiveFilter: (filter: string) => void;
  toggleSidebar: () => void;
}

export const useUIStore = create<UIState>((set) => ({
  sidebarOpen: false,
  activeFilter: 'all',
  setSidebarOpen: (sidebarOpen) => set({ sidebarOpen }),
  setActiveFilter: (activeFilter) => set({ activeFilter }),
  toggleSidebar: () => set((state) => ({ sidebarOpen: !state.sidebarOpen })),
}));
```

### Server State: TanStack Query (React Query)
* Caching, automatic refetching, optimistic updates, and offline resilience for dynamic client queries.

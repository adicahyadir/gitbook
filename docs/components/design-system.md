---
description: Design tokens, color palettes, typography scale, glassmorphic effects, and reusable component specifications.
---

# ACR Design System

The **ACR Design System** is an engineering-first design language prioritizing dark mode aesthetics, high-contrast clarity, glassmorphism, and fluid micro-interactions.

---

## 🎨 1. Color Palette & Semantic Tokens

Our color architecture relies on high-depth neutral obsidian backgrounds accented with crisp electric neons (Cyan, Violet, Emerald) to direct user attention.

### Core Swatches

| Token Name | Hex Code | HSL Value | Primary Usage |
| :--- | :--- | :--- | :--- |
| `--bg-base` | `#090D16` | `hsl(222, 44%, 6%)` | Root application background. |
| `--bg-surface` | `#111827` | `hsl(222, 38%, 11%)` | Cards, panels, elevated sheets. |
| `--bg-glass` | `rgba(17, 24, 39, 0.65)` | - | Glassmorphic floating surfaces. |
| `--border-subtle` | `rgba(255, 255, 255, 0.08)`| - | Structural dividing lines. |
| `--border-glow` | `rgba(99, 102, 241, 0.35)` | - | Active hover state borders. |
| `--accent-cyan` | `#06B6D4` | `hsl(189, 94%, 43%)` | Creative highlights, terminal accents. |
| `--accent-violet`| `#8B5CF6` | `hsl(258, 90%, 66%)` | Primary interactive buttons & active badges. |
| `--accent-emerald`| `#10B981`| `hsl(160, 84%, 39%)` | Success confirmations & healthy status pings.|

---

## 🔤 2. Typography Scale

* **Primary Sans:** [Inter](https://fonts.google.com/specimen/Inter) / System UI (`-apple-system`, `BlinkMacSystemFont`, `Segoe UI`).
* **Display / Brand:** [Outfit](https://fonts.google.com/specimen/Outfit) (Used for page titles and hero banners).
* **Monospace:** [JetBrains Mono](https://www.jetbrains.com/lp/mono/) (Used for code blocks, metrics, and API endpoints).

| Style | Tailwind Class | Font Size | Line Height | Tracking |
| :--- | :--- | :--- | :--- | :--- |
| **Hero Title** | `text-5xl md:text-6xl` | `3.75rem (60px)` | `1.1` | `-0.03em` |
| **Heading 1** | `text-3xl md:text-4xl` | `2.25rem (36px)` | `1.2` | `-0.02em` |
| **Heading 2** | `text-2xl` | `1.5rem (24px)` | `1.3` | `-0.01em` |
| **Heading 3** | `text-xl` | `1.25rem (20px)` | `1.4` | `normal` |
| **Body** | `text-base` | `1.0rem (16px)` | `1.6` | `normal` |
| **Small / Caption**| `text-sm` | `0.875rem (14px)` | `1.5` | `+0.01em` |
| **Code / Mono** | `text-xs font-mono` | `0.75rem (12px)` | `1.5` | `normal` |

---

## 🔮 3. Glassmorphism & Elevation Tokens

Glass surfaces use hardware-accelerated backdrops combined with translucent hairline borders:

```css
/* Glass Surface Utility */
.glass-panel {
  background: rgba(17, 24, 39, 0.65);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.08);
  box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
}

.glass-panel-hover:hover {
  border-color: rgba(139, 92, 246, 0.4);
  box-shadow: 0 12px 40px 0 rgba(139, 92, 246, 0.15);
}
```

---

## 🧩 4. Reusable UI Components

### Component: `Button`

The primary interactive action trigger. Supports subtle spring physics via Framer Motion, micro-glows, loading spinners, and icon slots.

#### Props Specification

| Prop | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `variant` | `'primary' \| 'secondary' \| 'glass' \| 'outline'` | `'primary'` | Visual hierarchy theme. |
| `size` | `'sm' \| 'md' \| 'lg'` | `'md'` | Padding and font size. |
| `isLoading` | `boolean` | `false` | Displays an animated spinner and disables clicks. |
| `leftIcon` | `ReactNode` | `undefined` | Icon element preceding label text. |
| `rightIcon` | `ReactNode` | `undefined` | Icon element following label text. |

#### Implementation

```tsx
// components/ui/Button.tsx
'use client';

import React, { ButtonHTMLAttributes, forwardRef } from 'react';
import { motion, HTMLMotionProps } from 'framer-motion';
import { cn } from '@/lib/utils';
import { Loader2 } from 'lucide-react';

export interface ButtonProps extends ButtonHTMLAttributes<HTMLButtonElement> {
  variant?: 'primary' | 'secondary' | 'glass' | 'outline';
  size?: 'sm' | 'md' | 'lg';
  isLoading?: boolean;
  leftIcon?: React.ReactNode;
  rightIcon?: React.ReactNode;
}

export const Button = forwardRef<HTMLButtonElement, ButtonProps>(
  (
    {
      className,
      variant = 'primary',
      size = 'md',
      isLoading = false,
      leftIcon,
      rightIcon,
      children,
      disabled,
      ...props
    },
    ref
  ) => {
    const baseStyles =
      'inline-flex items-center justify-center font-medium rounded-xl transition-all duration-200 focus:outline-none focus:ring-2 focus:ring-violet-500/50 disabled:opacity-50 disabled:cursor-not-allowed select-none active:scale-[0.98]';

    const variants = {
      primary:
        'bg-violet-600 hover:bg-violet-550 text-white shadow-lg shadow-violet-600/25 border border-violet-500/30 hover:shadow-violet-600/40',
      secondary:
        'bg-zinc-800 hover:bg-zinc-700 text-zinc-100 border border-zinc-700/50',
      glass:
        'bg-white/[0.05] hover:bg-white/[0.1] text-zinc-100 backdrop-blur-md border border-white/10 hover:border-white/20 shadow-sm',
      outline:
        'bg-transparent hover:bg-zinc-800/50 text-zinc-300 border border-zinc-700 hover:text-white',
    };

    const sizes = {
      sm: 'text-xs px-3 py-1.5 gap-1.5',
      md: 'text-sm px-4 py-2.5 gap-2',
      lg: 'text-base px-6 py-3 gap-2.5',
    };

    return (
      <button
        ref={ref}
        disabled={disabled || isLoading}
        className={cn(baseStyles, variants[variant], sizes[size], className)}
        {...props}
      >
        {isLoading ? (
          <Loader2 className="w-4 h-4 animate-spin" />
        ) : (
          leftIcon && <span className="inline-flex shrink-0">{leftIcon}</span>
        )}
        <span>{children}</span>
        {!isLoading && rightIcon && (
          <span className="inline-flex shrink-0">{rightIcon}</span>
        )}
      </button>
    );
  }
);

Button.displayName = 'Button';
```

---

### Component: `GlassCard`

Container element featuring ambient backdrop blur, light gradient sheen, and micro-hover elevation.

#### Implementation

```tsx
// components/ui/GlassCard.tsx
import React, { HTMLAttributes } from 'react';
import { cn } from '@/lib/utils';

export interface GlassCardProps extends HTMLAttributes<HTMLDivElement> {
  glow?: boolean;
}

export function GlassCard({
  className,
  glow = false,
  children,
  ...props
}: GlassCardProps) {
  return (
    <div
      className={cn(
        'relative rounded-2xl bg-zinc-900/60 backdrop-blur-xl border border-white/[0.08] p-6 shadow-xl transition-all duration-300 hover:border-violet-500/30 hover:shadow-2xl hover:shadow-violet-500/5',
        glow && 'before:absolute before:-inset-px before:rounded-2xl before:bg-gradient-to-r before:from-violet-500/20 before:to-cyan-500/20 before:opacity-0 hover:before:opacity-100 before:transition-opacity before:-z-10',
        className
      )}
      {...props}
    >
      {children}
    </div>
  );
}
```

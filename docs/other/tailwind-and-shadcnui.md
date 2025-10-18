# Tailwind CSS and shadcn/ui Overview

## 💨 Tailwind CSS

Tailwind CSS is a **utility-first** CSS framework, which means it provides a set of pre-designed **CSS classes** that you can use directly in your HTML code to style elements. Instead of writing custom CSS for every style, you apply these classes to HTML elements to control their appearance.

For example, if you want to make a paragraph bold and centered, you might use classes like `font-bold` and `text-center` directly in your HTML. This approach is popular because it speeds up development and keeps your styles consistent across a project.

**Key Concept:** Since only the classes you use are included in the final website, the CSS file becomes smaller. This makes websites load faster and improves performance. The unused styles are automatically removed during the build process.

## 🎨 shadcn/ui

shadcn/ui is not a traditional library you install as a dependency. It's a collection of beautifully designed, accessible, and customizable React components built on top of Radix UI primitives and styled with Tailwind CSS.

**Key Concept:** When you "install" a component (e.g., Button, Dialog) using the shadcn CLI, the actual TypeScript and React source code is copied directly into your project. This gives you complete ownership and control over the component code, allowing for deep customization without having to fight a library's abstraction.


## 📁 Typical Project Folder Structure

In a modern React/TypeScript project initialized with shadcn/ui, you'll see a specific structure emerge.

```
my-app/
├── src/
│   ├── App.tsx
│   ├── index.tsx
│   ├── components/
│   │   ├── ui/         # 🎨 shadcn/ui components reside here
│   │   │   ├── button.tsx
│   │   │   ├── dialog.tsx
│   │   │   └── card.tsx
│   │   ├── Navbar.tsx
│   │   └── Button.tsx
│   ├── hooks/
│   │   └── useAuth.ts
│   ├── types/
│   │   └── user.d.ts
│   ├── utils/
│   │   └── formatDate.ts
├── components.json     # 🎨 Configuration file for the shadcn/ui CLI
├── package.json
├── postcss.config.js   # 🎨 Tailwind implemented as a PostCSS plugin
├── tailwind.config.ts  # 🎨 Tailwind CSS configuration file
├── tsconfig.json
└── vite.config.ts

```

[Back to tech stack](tech-stack.md)
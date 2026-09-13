---
title: "unifiedTools"
parent: Variables
nav_order: 1
---


# Variable: unifiedTools

```ts
const unifiedTools: (
  | Tool<{
  includePrivate?: boolean;
  maxDepth?: number;
  path: string;
}>
  | Tool<{
  path: string;
  recursive?: boolean;
  threshold?: number;
}>
  | Tool<{
  className?: string;
  includeJsDoc?: boolean;
  name: string;
  path: string;
}>
  | Tool<{
  include?: "full" | "signature" | "methods-only" | "properties-only";
  includeJsDoc?: boolean;
  name: string;
  path: string;
}>)[];
```

Defined in: index.ts:369

All unified tools with auto-detection

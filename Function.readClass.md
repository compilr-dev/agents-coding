---
title: "readClass"
parent: Functions
nav_order: 1
---


# Function: readClass()

```ts
function readClass(
   path, 
   name, 
options?): Promise<ToolExecutionResult>;
```

Defined in: index.ts:250

Read a class by name

## Parameters

| Parameter | Type |
| ------ | ------ |
| `path` | `string` |
| `name` | `string` |
| `options?` | \{ `include?`: `"full"` \| `"signature"` \| `"methods-only"` \| `"properties-only"`; `includeJsDoc?`: `boolean`; \} |
| `options.include?` | `"full"` \| `"signature"` \| `"methods-only"` \| `"properties-only"` |
| `options.includeJsDoc?` | `boolean` |

## Returns

`Promise`\<`ToolExecutionResult`\>

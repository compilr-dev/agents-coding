---
title: "readType"
parent: Functions
nav_order: 1
---


# Function: readType()

```ts
function readType(
   path, 
   name, 
options?): Promise<ToolExecutionResult>;
```

Defined in: index.ts:314

Read a type, interface, or enum by name

## Parameters

| Parameter | Type |
| ------ | ------ |
| `path` | `string` |
| `name` | `string` |
| `options?` | \{ `includeJsDoc?`: `boolean`; \} |
| `options.includeJsDoc?` | `boolean` |

## Returns

`Promise`\<`ToolExecutionResult`\>

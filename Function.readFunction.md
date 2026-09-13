---
title: "readFunction"
parent: Functions
nav_order: 1
---


# Function: readFunction()

```ts
function readFunction(
   path, 
   name, 
options?): Promise<ToolExecutionResult>;
```

Defined in: index.ts:190

Read a function or method by name

## Parameters

| Parameter | Type |
| ------ | ------ |
| `path` | `string` |
| `name` | `string` |
| `options?` | \{ `className?`: `string`; `includeJsDoc?`: `boolean`; \} |
| `options.className?` | `string` |
| `options.includeJsDoc?` | `boolean` |

## Returns

`Promise`\<`ToolExecutionResult`\>

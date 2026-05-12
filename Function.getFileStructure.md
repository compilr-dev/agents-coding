---
title: "getFileStructure"
parent: Functions
nav_order: 1
---


# Function: getFileStructure()

```ts
function getFileStructure(path, options?): Promise<ToolExecutionResult>;
```

Defined in: index.ts:72

Get the appropriate getFileStructure tool for a file

## Parameters

| Parameter | Type |
| ------ | ------ |
| `path` | `string` |
| `options?` | \{ `includePrivate?`: `boolean`; `maxDepth?`: `number`; \} |
| `options.includePrivate?` | `boolean` |
| `options.maxDepth?` | `number` |

## Returns

`Promise`\<`ToolExecutionResult`\>

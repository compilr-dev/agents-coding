---
title: "getComplexity"
parent: Functions
nav_order: 1
---


# Function: getComplexity()

```ts
function getComplexity(path, options?): Promise<ToolExecutionResult>;
```

Defined in: index.ts:129

Get complexity metrics for a file

## Parameters

| Parameter | Type |
| ------ | ------ |
| `path` | `string` |
| `options?` | \{ `recursive?`: `boolean`; `threshold?`: `number`; \} |
| `options.recursive?` | `boolean` |
| `options.threshold?` | `number` |

## Returns

`Promise`\<`ToolExecutionResult`\>

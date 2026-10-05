---
name: code-conventions
description: Guidelines for writing readable code
---

# Overview

Write code so its structure and intent are quickly understood, rather than enforcing strict language-specific syntax or formatting.

Prioritize readability over mechanical rule-following. Prefer simpler, clearer expressions.

# Omitting Blocks for Embedded Statements

Omit a block only when the embedded statement is short and simple enough to be immediately understood on one line.

```csharp
// Good
if (isValid) Run();

// Bad
foreach (var route in EnumerateBranchRoutes(connections, branches))
    boltFittingPairs
        .AddRange(GetPairs(route, targetBranches));
```

# Separating Logical Code Groups

Use blank lines between logically distinct code groups.

```csharp
int width = GetWidth();
int height = GetHeight();

if (width <= 0 || height <= 0) return 0;

if (isRotated)
    (width, height) = (height, width);

int area = width * height;

return area;
```

# Breaking Long Lines

When a line's structure or meaning is hard to grasp at a glance, break it at syntactically meaningful boundaries.

Split sequences of elements or operations across lines to make their logical units clear.

```csharp
public ConnectionSessionService(
    IServerConnection connection,
    IServerModelCatalog catalog,
    ICodexCatalog codex,
    ILogger<ConnectionSessionService> logger,
    IConnectionRetryPolicy retryPolicy);

var result = service.Execute(
    request,
    options,
    sessionContext,
    cancellationToken,
    executionMetadata);

var items = source
    .Where(x => x.IsValid && x.IsEnabled)
    .OrderBy(x => x.Category)
    .ThenBy(x => x.Name)
    .Select(x => CreateItem(x, context))
    .ToList();

var connectionStatus = connection.IsConnected
    ? ConnectionStatus.Available
    : ConnectionStatus.Disconnected;
```

# Folder Structure

Group related code by feature and responsibility so it is easy to find and understand.

Create folders only when they help navigation or understanding. Avoid unnecessarily deep or fragmented hierarchies.

Do not force project-wide files into folders when they do not naturally belong to a specific feature or responsibility.

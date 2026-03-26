---
name: review-go-modern
description: Use when reviewing Go code in a production Go 1.25–1.26 service, especially when checking for modern idioms, concurrency safety, or error handling patterns
license: MIT
metadata:
  author: adrianhaj
  version: 1.0.0
  category: code-review
  tags:
    - golang
    - code-review
    - modern-go
---

Perform a thorough code review of the selected Go files in a production-grade
Go 1.25–1.26 codebase.

Follow these steps:

1. Understand the change
   - Read the diff and surrounding code.
   - Infer the intent of the change (bug fix, feature, refactor).

2. Check correctness and safety
   - Look for data races, panic-prone patterns, incorrect error handling,
     misuse of `context.Context`, and unsafe concurrency.

3. Check performance
   - Identify obvious allocation hot spots, unnecessary copies, repeated work,
     and misuse of goroutines (too many / too few / blocking).

4. Concurrency patterns (Go 1.25 WaitGroup.Go)
   - Look for manual `WaitGroup.Add`/`Done` pairs and consider whether they can
     be simplified with `WaitGroup.Go` (Go 1.25+).
   - If switching to `WaitGroup.Go` reduces the risk of mismatched counters and
     improves readability, suggest the change with a small before/after snippet.

5. Error handling (Go 1.26 errors.AsType)
   - Prefer `errors.AsType[E]` over `errors.As` for type-safe error checking in
     new or modified code.
   - When you see `errors.As` plus a temporary pointer variable, suggest an
     equivalent `errors.AsType` form and explain why it is safer and clearer.

6. Syntax modernization (Go 1.26 new(expr))
   - Highlight places where a temporary variable is created only to take its
     address and can safely be replaced with `new(expr)`.
   - Show a concrete before/after example and confirm behavior is unchanged.

7. Produce the review
   - Start with a short summary.
   - Group findings under: Bugs, Concurrency, Performance, API & Maintainability,
     Modern Go (1.25–1.26 idioms).
   - For each finding provide:
     - A short title and severity.
     - A concise explanation.
     - A minimal suggested fix (code snippet or diff-style block).
   - If the code is already in good shape, state that explicitly and list at
     most 3 small improvements.

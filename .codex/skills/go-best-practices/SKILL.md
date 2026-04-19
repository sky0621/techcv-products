---
name: go-best-practices
description: Write, review, or refactor Go source files and go.mod changes with idiomatic Go patterns, conservative API changes, clear error handling, and project-local consistency. Use when working on .go files, module wiring, tests, interfaces, concurrency, or package boundaries in Go repositories.
---

# Go Best Practices

Keep changes idiomatic, local, and easy to verify. Match the repository's existing package layout, naming, and test style before introducing new patterns.

## Working Style

- Read nearby files before editing. Follow existing receiver style, constructor patterns, package layout, and test conventions.
- Prefer small, explicit changes over framework-like abstractions.
- Keep exported APIs stable unless the task requires a breaking change.
- Return concrete structs and accept narrow interfaces when abstraction is actually needed.
- Keep functions focused. Split long functions when a named helper makes the behavior clearer.

## Types And Package Design

- Use named types for domain values that should not be mixed accidentally, such as IDs or status values.
- Keep interfaces close to the consumer package. Do not create broad interface layers "just in case".
- Use composition over deep inheritance-style embedding. Embed only when the promoted fields or methods are genuinely part of the type.
- Keep package boundaries clear. Avoid circular dependencies and avoid pushing unrelated helpers into shared utility packages.

## Errors And Control Flow

- Return errors instead of panicking, except for truly unrecoverable startup invariants.
- Wrap returned errors with `%w` when additional context helps the caller.
- Use sentinel errors sparingly. Prefer typed context and `errors.Is` or `errors.As` where they improve call-site behavior.
- Keep happy-path flow shallow. Use early returns to avoid nested conditionals.
- Handle zero values intentionally. If a zero value is invalid, enforce that in constructors or validation helpers.

## Context, IO, And Concurrency

- Pass `context.Context` as the first parameter for request-scoped or cancelable work. Do not store contexts in structs.
- Propagate deadlines and cancellation through outbound calls.
- Make goroutine ownership explicit. Every started goroutine should have a clear shutdown path.
- Protect shared mutable state with channels or synchronization primitives. Avoid mixing both without a reason.
- Be careful with loop variable capture and concurrent writes to maps or slices.

## Tests And Verification

- Add or update the smallest relevant tests when behavior changes.
- Prefer table-driven tests when multiple cases share the same behavior shape.
- Keep tests deterministic. Avoid real time, network, and sleep-based assertions when a fake or injected dependency works.
- When changing public behavior, verify both success and failure paths.
- Run `gofmt` on touched Go files and use the smallest relevant Go test command available in the repository.

## Common Review Heuristics

- Check whether a new interface can be removed.
- Check whether an exported symbol can stay unexported.
- Check whether error messages identify the failed operation clearly.
- Check whether a new helper improves readability more than it fragments logic.
- Check whether a concurrent path can leak goroutines, ignore context cancellation, or race on shared state.

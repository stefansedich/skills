---
name: refactor
description: Refactor code following clean code principles — favour simplicity over complexity, reduce duplication, and always present a plan before making changes. Use when the user asks to "refactor", "clean up", "simplify", "reduce duplication", "restructure", "tidy up", "improve code quality", or otherwise wants code improved without changing behaviour.
---

# Refactoring

Refactor code to be simpler, clearer, and free of unnecessary duplication — without changing observable behaviour.

## Core principles

1. **Simplicity over complexity** — prefer the straightforward solution. Remove abstractions that don't earn their keep.
2. **DRY (Don't Repeat Yourself)** — extract shared logic; eliminate copy-paste code.
3. **Single Responsibility** — each function, class, or module should do one thing well.
4. **Meaningful names** — variables, functions, and types should reveal intent.
5. **Small functions** — if a function needs a comment to explain *what* it does, it should be split or renamed.
6. **Minimal surface area** — remove dead code, unused parameters, and unnecessary exports.
7. **Favour composition over inheritance** — build behaviour from small, composable parts.
8. **Least surprise** — code should behave as a reader would expect from its name and structure.

## Workflow — plan first, always

Before touching any code, **present a refactoring plan** to the user and wait for approval.

### Step 1: analyse

- **Code smells** — duplication, long methods, deep nesting, feature envy, primitive obsession, shotgun surgery, etc.
- **Simplification opportunities** — over-engineered abstractions, unnecessary indirection, complex conditionals that can be flattened, convoluted control flow, or overly clever code that could be rewritten plainly.
- **Duplication** — repeated logic across functions, modules, or files; copy-paste patterns; near-identical code paths that differ only in minor details.
- **Best-practice gaps** — idiomatic patterns for the language/framework not being followed, missing error handling, inconsistent naming, poor separation of concerns, misuse of APIs, or anti-patterns specific to the ecosystem (e.g., callback hell in async code, mutable shared state where immutability is preferred).
- **Behavioural contract** — note which behaviour must be preserved (inputs → outputs, side effects, public API contracts).
- **Scope** — list affected files and their relationships.

### Step 2: present the plan

Output a concise plan that includes:

1. **Goal** — one sentence stating the refactoring objective.
2. **Issues found** — bullet list of specific problems, grouped by category (smells, simplification opportunities, duplication, best-practice gaps).
3. **Proposed changes** — ordered list of refactoring steps (e.g., "Extract method X from Y", "Inline temporary variable Z", "Replace conditional with polymorphism in A", "Adopt idiomatic pattern P in module M").
4. **Risk assessment** — anything that could change behaviour or break dependents.
5. **Verification** — how correctness will be confirmed (existing tests, new tests, manual check).

Do **not** proceed until the user confirms or adjusts the plan.

### Step 3: implement

- Apply changes incrementally — one refactoring move at a time where practical.
- **Parallelise where possible** — when the plan contains independent refactoring steps (touching separate files or modules with no mutual dependencies), execute them in parallel using sub-agents if available. Only serialise steps that depend on each other's output.
- Run existing tests (or suggest running them) after each logical step.
- Keep commits atomic: one refactoring concept per commit when possible.

### Step 4: verify

- Run the full test suite.
- Summarise what changed and confirm behaviour is preserved.

## Refactoring techniques (reference)

Apply the most appropriate technique for each issue:

| Issue | Technique |
|-------|-----------|
| Duplicated code | Extract Method / Extract Function |
| Long method | Split into smaller functions |
| Deep nesting | Early return / Guard clauses |
| Large class | Extract Class / Split Module |
| Feature envy | Move Method to the class it envies |
| Primitive obsession | Introduce Value Object / Type |
| Long parameter list | Introduce Parameter Object |
| Shotgun surgery | Move related logic together (cohesion) |
| Dead code | Delete it |
| Comments explaining *what* | Rename / Extract to make code self-documenting |
| Over-abstraction | Inline and simplify; remove unnecessary layers |
| Complex conditionals | Simplify with lookup tables, early returns, or polymorphism |
| Non-idiomatic code | Rewrite using language/framework conventions |
| Inconsistent error handling | Adopt a uniform strategy (e.g., Result types, error middleware) |
| Mutable shared state | Prefer immutability or encapsulate mutation behind clear boundaries |
| Callback / promise soup | Convert to async/await or equivalent structured concurrency |
| Near-duplicate code paths | Parameterise differences and unify into a single implementation |

## What not to do

- Do not change behaviour or public APIs unless explicitly asked.
- Do not gold-plate — stop when the code is clear and duplication-free.
- Do not refactor and add features in the same step.
- Do not skip the plan step, even for "obvious" cleanups.

## Exiting refactor mode

Return to normal operation when the user says "done", "stop refactoring", "that's enough", or moves on to an unrelated task.

# Week 2 Spec-Driven Development Write-up

## Project context

This project followed the Spec Kit workflow for the quote-of-the-day feature: constitution, specification, planning, task generation, implementation, and convergence. The repository evidence for the generated artifacts is in [.specify/memory/constitution.md](.specify/memory/constitution.md), [specs/002-quote-of-day/spec.md](specs/002-quote-of-day/spec.md), [specs/002-quote-of-day/plan.md](specs/002-quote-of-day/plan.md), [specs/002-quote-of-day/tasks.md](specs/002-quote-of-day/tasks.md), and the implementation in [index.html](index.html), [styles.css](styles.css), and [script.js](script.js).

## Actual Spec Kit prompts and stage evidence

### Constitution
- Prompt text recorded in the assignment instructions: "/speckit-constitution Create principles focused on code quality, testing, and maintainability."
- Evidence: the governing constitution exists at [.specify/memory/constitution.md](.specify/memory/constitution.md) and includes the project principles and version metadata.

### Specify
- The exact natural-language prompt for this stage is not preserved as a standalone record in the repository.
- Evidence: the final specification in [specs/002-quote-of-day/spec.md](specs/002-quote-of-day/spec.md) captures the feature intent, user stories, functional requirements, edge cases, and success criteria.

### Plan
- The exact natural-language prompt for this stage is not preserved in the repository.
- Evidence: the plan document exists at [specs/002-quote-of-day/plan.md](specs/002-quote-of-day/plan.md) and documents the browser-only architecture, storage approach, and validation considerations.

### Tasks
- The exact natural-language prompt for this stage is not preserved in the repository.
- Evidence: [specs/002-quote-of-day/tasks.md](specs/002-quote-of-day/tasks.md) contains the dependency-ordered task breakdown and indicates the implementation status for each task.

### Implement
- The exact natural-language prompt for this stage is not preserved in the repository.
- Evidence: the implementation is present in [index.html](index.html), [styles.css](styles.css), and [script.js](script.js), and the browser validation performed later confirms the main interactions work.

### Converge
- The exact natural-language prompt for this stage is not preserved in the repository.
- Evidence: no standalone convergence transcript or result file was located in the workspace. The implementation and the specification artifacts are aligned, but the exact converge output text was not captured in repository evidence.

## Before/after refinement and its impact

### Before
The starting requirement was a broad user-facing description: a quote-of-the-day page with a random quote, a “New quote” action, and favorites that persist after the page reloads. That description defined the intent, but it did not yet include the structured user stories, measurable acceptance criteria, or explicit empty-state rules that later made the feature testable.

### After
The final specification in [specs/002-quote-of-day/spec.md](specs/002-quote-of-day/spec.md) expands that broad idea into a concrete implementation target:

- Four user stories covering display, quote rotation, persistence, and favorite management.
- Eleven functional requirements, including FR-011 for empty or invalid quote collections.
- Six success criteria covering valid display, quote rotation, persistence, and empty-state behavior.
- Explicit edge cases and acceptance scenarios for empty, invalid, and malformed states.

### Impact
This refinement changed the project from a vague request into a design specification that could drive implementation and validation in [specs/002-quote-of-day/plan.md](specs/002-quote-of-day/plan.md) and [specs/002-quote-of-day/tasks.md](specs/002-quote-of-day/tasks.md). The main improvement was not a redesign of the app; it was the addition of unambiguous rules for when the quote collection is empty, invalid, or missing, which made the expected behavior clearer and easier to assess.

## Evidence from implementation and browser validation

The app in [index.html](index.html), [styles.css](styles.css), and [script.js](script.js) implements a static browser page with a built-in quote collection, a “New quote” button, and favorite persistence using browser local storage.

The browser validation I actually executed in the running page showed the following:

- A quote is displayed on load.
- The “New quote” action changes the visible quote.
- The favorite button toggles the current quote into and out of the saved favorites list.
- The saved favorite IDs persist in localStorage and remain available after a page reload.

These checks were performed against the local page at http://localhost:8000 and produced consistent results with the app logic, including a valid state transition from the current quote to a different quote and then to a persisted favorite state after reload.

The empty-collection and invalid-collection scenarios were not independently browser-tested in this environment because the current implementation uses a top-level quote array rather than a runtime source that can be swapped or empty at runtime. The corresponding guard logic in [script.js](script.js) was reviewed as code inspection evidence, but I am not claiming a live browser test for those failure paths.

## Reflection

Spec-Driven Development felt like overhead when the feature was small and the requirement was already obvious, because the planning and task artifacts added process on top of a straightforward browser page. It paid off when the work required clear rules for persistence and empty states, because those details reduced ambiguity and made validation easier to reason about. In this project, the design artifacts were most useful as a guardrail against accidental drift in the feature behavior. Overall, the process was heavier than the code itself, but it made the feature easier to review and maintain.

## Limitation and evidence boundary

The repository does not preserve a separate, verbatim transcript for the Plan, Tasks, Implement, or Converge prompts. The available evidence supports the output artifacts and the implementation itself, but it does not provide a complete literal record of every Spec Kit command used during the workflow. For this reason, the write-up distinguishes between recorded prompts, generated artifacts, code inspection, and browser-tested behavior rather than treating all stages as equally evidenced.

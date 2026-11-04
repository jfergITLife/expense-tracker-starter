# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Starter project for a Claude Code course: a basic expense tracker built with React 19 and Vite, written in plain JavaScript (no TypeScript). The README says it intentionally has a bug, poor UI, and messy code, which get fixed during the course. Expect rough code, and don't treat existing patterns as conventions to preserve.

## Commands

```bash
npm install
npm run dev      # dev server at http://localhost:5173
npm run build    # production build to dist/
npm run preview  # serve the production build
npm run lint     # ESLint
```

No test framework is configured, so there are no tests to run.

## Architecture

All application logic is in one component, `src/App.jsx`: the transaction list, form fields, filters, derived totals, and all rendering. `src/main.jsx` only mounts it inside `StrictMode`.

- **State:** local `useState` only. Transactions start from a hardcoded array and aren't persisted, so changes are lost on reload.
- **Derived values:** totals and the filtered list are recalculated on each render rather than stored in state.
- **Amounts are numbers:** `amount` is a number on every transaction. The form's `amount` state is a string because it holds the input's value, so `handleSubmit` converts it with `Number()` when creating a transaction.
- **Styling:** plain CSS, with global base styles in `src/index.css` and app styles in `src/App.css`.

## Git remotes

`origin` is the upstream course repo, and this account can't push to it (403). Push to `github-personal` (`jfergITLife/expense-tracker-starter`) and open PRs there.

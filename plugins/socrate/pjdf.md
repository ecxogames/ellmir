## Task
- Convert the provided HTML into an engine-ready fragment.
- JSON files are already provided by the engine as JavaScript object variables. Never fetch or load JSON.
- Replace references like `fetch('manifest.json')` with direct use of `manifest`, and `fetch('guide.json')` with direct use of `guide`.
- Remove related `fetch`, `.json()`, response checks, and unnecessary async/await.
- Preserve all other styling, markup, and functionality.

## Input
- Trigger: `ellmir.plugins.socrate.pjdf`
- Source: One HTML file.

## Output
- Keep exactly one `<style>`, one `<div>`, and one `<script>`, in that order.
- Remove document wrappers such as `<!DOCTYPE>`, `<html>`, `<head>`, and `<body>`.
- Never call, fetch, parse, or load JSON files.
- Assume JSON objects like manifest and guide already exist globally.

## Examples
- Parsed data.apps from `manifest.json` → `manifest.apps`.
- Parsed data.steps from `guide.json` → `guide.steps`.
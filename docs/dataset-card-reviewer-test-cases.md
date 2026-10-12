# Dataset Card Reviewer - Manual Test Cases

## Overview

This document records manual tests for the dataset-card-reviewer
example, covering valid, missing, empty, and unreadable inputs.

Tests were performed using docs/dataset-card-reviewer.html.
The browser checker accepts JSON inputs only.

## Test 1: Complete Dataset Card

Input:
```json
{
  "name": "toy-cards",
  "license": "cc-by-4.0",
  "tasks": ["text-classification"]
}
```

Expected result:
- All three required fields are present and nonempty.
- No missing or empty fields.
- No structural changes required.
- License rights and compatibility are not verified.

Observed result: Matched expectations.

## Test 2: Missing License and Empty Tasks

Input:
```json
{
  "name": "toy-cards",
  "tasks": []
}
```

Expected result:
- Name is present and nonempty.
- License is reported as missing.
- Tasks is reported as empty.
- The report recommends fixing only the flagged fields.

Observed result: Matched expectations.

## Test 3: Unreadable JSON

Input:
```json
{
  "name": "toy-cards",
  "license": "cc-by-4.0",
  "tasks": ["text-classification"]
```

Expected result:
- JSON parsing fails.
- The reviewer requests valid JSON syntax.
- No code is executed.

Observed result: The checker reported:
"Could not parse JSON. Check commas, quotes and brackets.
No code was executed."

## Test 4: Empty Tasks Only

Input:
```json
{
  "name": "toy-cards",
  "license": "cc-by-4.0",
  "tasks": []
}
```

Expected result:
- Name and license are present and nonempty.
- No fields are missing.
- Tasks is reported as empty.
- The report recommends fixing only the tasks field.

Observed result: Matched expectations.

## Limitations

- These are manual browser-based tests, not automated tests.
- The browser checker supports JSON, while SKILL.md also
  describes YAML and Python-dictionary-style cards.
- Checking whether a license field is nonempty does not
  establish legal validity, redistribution rights, or
  license compatibility.

## Conclusion

All four manual test cases produced the expected results.
The examples clarify the distinction between missing,
empty, and unreadable inputs.
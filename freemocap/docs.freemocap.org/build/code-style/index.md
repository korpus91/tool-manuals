# Python code style | FreeMoCap

Skip to main content

This page is in flux. Code style section for FreeMoCap core is a work in progress for version alpha. It's expected to stabilize by beta.
Human-checked documentationchecked against source

This page is adapted from real, human-written FreeMoCap documentation. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

freemocap v2.0.0-alpha.21: .pre-commit-config.yaml (black 22.6.0 hook), .flake8, CONTRIBUTING.md, pyproject.toml/poe_tasks.toml (ruff, pytest), CI workflow, and source spot-checks for docstring/type-hint/naming conventions

2026-08-19

v1 (ported, not yet re-checked against v2)

More about how these docs are written

# Python code style guide

This style guide aims to maintain code readability, quality, and maintainability.

## General guidelines​

- Follow a Universal Design approach that aspires to be interpretable to the widest possible number of people

- Follow PEP 8 Guidelines

- Follow standard best practices, for example SOLID, and so on

- Use Black to auto-format your code

## Specific guidelines​

-
Include Google-formatted docstrings: use Google-style docstrings for functions, methods, and classes to provide clear and concise documentation.

-
Type hints: use input and return type hints for functions and methods to improve code readability and facilitate better tooling support.

-
Keyword arguments: prefer using keyword arguments over simple arguments for functions and methods to improve code clarity.

-
Private methods and attributes: use leading underscores to denote private methods and attributes in classes, and use @property decorators when appropriate.

-
Descriptive names: use full words in variable and class names instead of abbreviations (for example, database instead of db).

-
PEP8 and black formatting: follow PEP8 and black code formatting guidelines to maintain consistency and readability.

-
Consistent naming conventions: adopt consistent naming conventions for variables, functions, and classes.

- Use snake_case for variables and functions (for example, my_variable, my_function)

- Use PascalCase for class names (for example, MyClass)

- Use UPPERCASE for constants (for example, MY_CONSTANT)

-
Keep functions and methods short: aim to keep functions and methods concise, ideally not exceeding 15-20 lines of code.

-
Modularize code: organize code into modules and packages to maintain a clean and organized codebase.

-
Minimal comments: avoid comments if possible. Write code that is simple and descriptive (See pt 5) enough that comments are not necessary. If needed, use comments sparingly to provide context or explain complex or non-obvious sections of your code.

-
Error handling: use appropriate error handling techniques, such as try and except blocks, to handle exceptions and provide meaningful error messages to users.

-
Write tests: write unit tests to ensure the correct functioning of your code.

-
Code reviews: perform code reviews with team members or peers to maintain a high-quality codebase.

- General guidelines

- Specific guidelines

# Copilot Instructions for ZavaLabFork

## Project Overview

This is the **ZavaStorefront** project — an ASP.NET Core MVC web application (.NET 6.0) that simulates an e-commerce storefront for "Zava." The codebase includes:

- **`src/`** — The .NET web application (controllers, models, services, views, static assets).
- **`infra/`** — Azure infrastructure as code (Bicep templates) provisioning App Service, ACR, Managed Identity, Monitoring, and AI Foundry.
- **`docs/`** — Lab exercise documentation (Markdown), organized by exercise number.
- **`.github/workflows/`** — GitHub Actions CI/CD workflows.
- **`azure.yaml`** — Azure Developer CLI (azd) configuration for deployment.

## Exercise Workflow

We are working through a series of hands-on lab exercises. Follow these rules strictly:

### 1. One Key Task at a Time
- The user will provide a markdown file for an exercise. Each exercise contains multiple Key Tasks.
- **Work through each Key Task one at a time.** Do not skip ahead or combine Key Tasks.
- Complete the current Key Task fully before moving on.

### 2. Key Task Completion & Validation
- After completing a Key Task, confirm what was done and verify there are no errors.
- If there are errors, work with the user to debug and resolve them before proceeding.
- Do not move to the next Key Task until the current Key Task is error-free.

### 3. Moving Between Key Tasks
- Once a Key Task is complete, either:
  - **You** ask the user if they are ready to move on to the next Key Task, or
  - **The user** tells you to move on to the next Key Task.
- Wait for explicit confirmation before starting the next Key Task.

### 4. Moving Between Exercises
- We will iterate through multiple exercise markdown files until the full set of exercises is complete.
- When all Key Tasks in an exercise are finished, wait for the user to provide the next exercise markdown file.

### 5. Debugging Together
- If something goes wrong at any Key Task, do not silently move on. Surface the issue clearly.
- Propose fixes and work collaboratively with the user to resolve problems.

### 6. General Guidelines
- Read each Key Task's instructions carefully before executing.
- Use the project structure and context above to inform your actions.
- Prefer making changes directly (editing files, running commands) over just suggesting them, unless the Key Task calls for manual action outside of the IDE.
- Keep the user informed of progress with concise updates.

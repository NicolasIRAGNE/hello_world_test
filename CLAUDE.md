# 91 - Step coding

You are currently in an isolated environment and run 8 at the step coding.

Your current context dir is:

context/task/coding/8

Any work you do MUST be saved in the context dir.
Inside context, you will find a list of directories with general context for the project.

--- PROJECT'S CLAUDE.MD BELOW ---

**Stack Guidelines for the AI Agent**

1. **Language:**

   * Python (version ≥ 3.11 recommended).
   * Strict typing required; avoid untyped functions unless absolutely necessary.

2. **Environment & Dependency Management:**

   * Use **uv** for environment creation, dependency installation, and script running.
   * No manual `venv` creation or `pip install` — all handled via uv (eg. `uv venv`)

3. **Framework:**

   * **FastAPI** for building the web API.
   * API should expose OpenAPI documentation and use Pydantic for request/response validation.

4. **State Management:**

   * Use the **`transitions`** library (with an “s”) to implement finite state machines.
   * Define states and transitions explicitly, avoid implicit state changes.

5. **Project Practices:**

   * Code should be modular but minimal, this is a MvP and we should avoid any unecessary complexity
   * NEVER write unit tests, testing is doubting, big redflag imho
   * Follow clean coding conventions and clear documentation for any public interfaces.
   * use Context7 MCP when interacting with a library
   * Do NOT try to maintain compatibility when implementing new changes. Change all relevant files to use the new changes.
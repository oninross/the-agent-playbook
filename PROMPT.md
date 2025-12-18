# AGENT INSTRUCTION: WORKFLOW ORCHESTRATION

**Role of the Foreground Agent (Intake & Discovery):**
You must act as a Project Manager. You are strictly forbidden from asking multiple questions at once. You must wait for a user response after every single question before proceeding to the next step.

### Phase 0: Initialisation

Display the following greeting and ASCII art immediately upon starting:

"Welcome, Developer. Let's get started on your component."

### Phase 1: Sequential Intake

Follow this exact order, asking only one question at a time:

1. Ask for the **Component Name** (the exact name for the React component). Wait for response.
2. Ask for the **Category** (Atom, Molecule, or Organism). Wait for response.
3. Ask "Should I use Shadcn UI as a base for this component? (I will install it if missing)". Wait for response.
4. Ask for the **Figma Link** (the URL of the specific design frame). Wait for response.

### Phase 2: Sequential Infrastructure Decisions

Follow this logic for framework requirements:

1. **Storybook Decision:**

   - Ask: "Would you like to add Stories for this component?"
   - **If NO:** Set Storybook Status to SKIP.
   - **If YES:** Scan the workspace for a `.storybook` directory or `main.ts`.
     - If found: Set Storybook Status to PROCEED.
     - If NOT found: Ask "Storybook is missing. Would you like me to install it now?" If yes, set to INSTALL_FRAMEWORK; if no, set to SKIP.
   - Wait for the user's final decision before moving to the next check.

2. **Testing Decision:**
   - Ask: "Would you like to add unit testing for this component?"
   - **If NO:** Set Testing Status to SKIP.
   - **If YES:** Scan the workspace for `vitest.config.ts` or `jest.config.js`.
     - If found: Set Testing Status to PROCEED.
     - If NOT found: Ask "A testing framework is missing. Would you like me to install Vitest now?" If yes, set to INSTALL_FRAMEWORK; if no, set to SKIP.
   - Wait for the user's final decision before proceeding.

### Phase 3: Retrieval & Handoff

Only after the developer provides all details and makes framework decisions:

1. **Retrieve Design:** Use MCP tools to extract data from the provided Figma Link.
2. **Handoff:** Package the user preferences, discovery results, and Figma data. Pass them to the **Background Agent / CGA** as system instructions.

---

---

### Context for Component Generator Agent (CGA)

**Target:** [NAME_FROM_INTAKE]
**Category:** [CATEGORY_FROM_INTAKE]
**Shadcn UI:** [YES/NO]
**Storybook Status:** [PROCEED / INSTALL_FRAMEWORK / SKIP]
**Testing Status:** [PROCEED / INSTALL_FRAMEWORK / SKIP]

**0. INFRASTRUCTURE SETUP (EXECUTE FIRST)**

- **If Shadcn YES:** Check for `components.json`. If missing, run `npx shadcn@latest init`.
- **Component Mapping:** Analyze [INJECTED_DESIGN_DATA_FROM_MCP]. If the design matches a Shadcn primitive (Badge, Button, Input, etc.), run `npx shadcn@latest add [primitive_name]`.

**1. MANDATORY RULES (AGENTS.md & SKILLS.md)**

- **File Structure:** Create the folder `src/components/[Category]/[Name]/`.
- **The Bundle:** Generate all required files (up to 6) including `index.ts`, `.tsx`, `.styles.scss`, `.types.ts`.
- **Composition Rule:** If Shadcn is YES, do NOT build primitives from scratch. Import the relevant Shadcn component and wrap/extend it with your BEM SCSS and Tailwind classes.
- **Styling:** Use BEM methodology and Design Tokens from `variables.css`.
- **Shadcn Composition:** \* **If Shadcn UI is YES:** Identify the closest Shadcn primitive (e.g., Badge, Button). Install it via CLI and use it as the base wrapper for your JSX.
  - **If Shadcn UI is NO:** Build the component using standard HTML elements (div, button, span, etc.) based strictly on Figma data.
- **Styling:** Use BEM methodology and Design Tokens from `variables.css`.
- **Hybrid Styling:** If Shadcn is YES, use Tailwind for the base primitive and BEM SCSS for custom overrides.
- **Hybrid Rule:** Use Tailwind for Shadcn primitives and BEM SCSS for custom overrides.

**2. Design Context**
[INJECTED_DESIGN_DATA_FROM_MCP]

**CGA Final Action:** 1. Execute necessary installs based on framework decisions. 2. If Shadcn is YES, wrap the primitive. If NO, build from scratch. 3. Generate the full component bundle in a single output without code comments.

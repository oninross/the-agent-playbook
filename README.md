# ⚛️ AI-Driven React Component Library (TypeScript, SCSS, BEM)

A highly structured and opinionated component library built on the Atomic Design methodology. This project maintains a professional, accessible, and high-quality codebase through strict adherence to **Design Tokens**, **BEM styling**, **TypeScript strict mode**, and **80%+ test coverage**.

---

## 📖 Key Documentation

The foundation of this repository is defined in two critical documents:

| Document                     | Purpose                                                                                                                                                              | Audience                           |
| :--------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------- |
| **[AGENTS.md](./AGENTS.md)** | **AI Assistant Implementation Guide.** Detailed, step-by-step instructions for AI agents on component structure, styling rules, testing, and mandatory restrictions. | AI Assistants, Automated Tools     |
| **[SKILLS.md](./SKILLS.md)** | **Required Developer Skills & Competencies.** Outlines the expected knowledge base in React, TypeScript, Testing (Vitest/RTL), SCSS, and Accessibility.              | Human Developers, New Contributors |

---

## 🚀 Getting Started

Follow these steps to set up the project locally.

### Prerequisites

- Node.js (LTS version)
- npm (or yarn/pnpm)

### Installation

1.  Clone the repository:
    ```bash
    git clone [YOUR-REPO-URL]
    cd [YOUR-REPO-NAME]
    ```
2.  Install dependencies:
    ```bash
    npm install
    ```

## 🛠️ Available Commands

| Command             | Purpose                                                   |
| :------------------ | :-------------------------------------------------------- |
| `npm run storybook` | Starts the Storybook development server (view components) |
| `npm run build`     | Builds the component library for distribution (Rollup)    |
| `npx vitest`        | Runs all unit tests with Vitest (target 80% coverage)     |
| `npm run lint`      | Lints source files with ESLint                            |
| `npm run format`    | Formats all code using Prettier                           |

---

## 🏗️ Component Structure Mandate

All components **MUST** adhere to the mandatory 5-file structure and be organized by Atomic Design category.

### Example: `src/components/atoms/Button/`

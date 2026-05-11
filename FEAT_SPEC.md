# Feature Specification: [Feature Name]

## 1. Document Context

- **Feature ID:** `FEAT-001`
- **Source:**
  - **Screenshot:** `[FILENAME].png`
  - **Guidelines:** `[Link to Design System]`
- **Architecture:** `[e.g., Clean Architecture / MVC]`

---

## 2. Functional Specification (The "What")

### 2.1 User Story

As a **[User Role]**, I want to **[Action]** so that **[Benefit]**.

### 2.2 Acceptance Criteria

- [ ] **Scenario 1:** [Input] -> [Expected Result]
- [ ] **Scenario 2:** [Error Case] -> [Validation Message]

---

## 3. Design Specification (The "Look")

> **Instruction for AI:** Analyze the attached screenshot `[FILENAME].png` for layout and spacing.

### 3.1 Component Mapping

- **Layout:** [e.g., Flexbox row with 24px gap]
- **Styling:** Use tokens from `@/styles/design-system`
- **Assets:** Use icons from `lucide-react`

---

## 4. Technical Implementation (The "How")

### 4.1 Data Structures

```typescript
export interface FeatureState {
  id: string;
  status: "idle" | "loading" | "error";
}
```

### 4.2 Implementation Checklist

1. [ ] Create `components/FeatureView.tsx`
2. [ ] Implement `useFeatureHook.ts` for state management
3. [ ] Integrate with `POST /api/v1/resource`

---

## 5. Automated Validation

- **Unit Test:** Ensure `handleAction` triggers the correct state change.
- **Visual Test:** Layout must match the reference image provided in Section 1.

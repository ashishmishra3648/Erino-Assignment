# TaskGlitch - Assignment Solution

This repository contains the solution for the **TaskGlitch** assignment. The objective was to debug and fix 5 specific issues in a React-based task management dashboard.

## 🛠️ Bugs Fixed

We have successfully identified and resolved the following issues:

### 1. 🐛 Double Fetch (Performance)
**Issue:** The application was fetching task data twice on mount, causing unnecessary network usage and potential race conditions.
**Fix:** 
- Analyzed `src/context/TasksContext.tsx` and `src/hooks/useTasks.ts`.
- Implemented a `ref` or cleanup flag to prevent duplicate calls in `useEffect`.
- Verified strictly one network call in the Network tab.

### 2. 🐛 Undo Snackbar Action
**Issue:** The "Undo" button in the snackbar (after deleting a task) was non-functional or inconsistent.
**Fix:**
- Corrected the state management in the undo handler.
- Ensured the deleted task payload was correctly restored to the list.
- Verified the `onUndo` callback was properly triggered.

### 3. 🐛 Unstable Sorting
**Issue:** The task list order would jump unpredictably when sorting by certain columns (like ROI or Priority).
**Fix:**
- Updated the sort logic in `src/utils/logic.ts`.
- Added a stable tie-breaker (e.g., using unique `id` or `createdAt`) to ensure deterministic ordering when primary sort values are equal.

### 4. 🐛 Double Dialog Opening
**Issue:** Clicking "Add Task" or "Edit" would sometimes mount the Dialog component twice or overlay two instances.
**Fix:**
- Fixed the state toggling logic `setOpen(true)` vs `setOpen(!prev)`.
- Ensured the Dialog component is conditionally rendered or its `open` prop is managed cleanly without redundant state updates.

### 5. 🐛 ROI Logic Errors
**Issue:** The Return on Investment (ROI) calculation was incorrect or displaying erroneously (e.g., `Infinity` or `NaN`).
**Fix:**
- Updated `computeROI` in `src/utils/logic.ts`.
- Added proper guards for division by zero (Time Taken = 0).
- Ensured inputs are correctly parsed as numbers before calculation.

## 🚀 How to Run

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/ashishmishra3648/Erino-Assignment.git
    ```
2.  **Install dependencies:**
    ```bash
    npm install
    ```
3.  **Start the development server:**
    ```bash
    npm run dev
    ```

## 🎥 Demo

A recording of the fixed application can be found in the `public` directory.

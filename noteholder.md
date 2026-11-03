# User Requirement Document (URD)
**Project Name:** Portable Single-File Note Manager
**Status:** Finalized Requirements
**Document Version:** 1.0

---

## 1. Project Overview
### 1.1 Vision
The goal is to create a lightweight, highly portable, single-file web application designed for quick, session-based note management. The application allows users to organize, edit, and export notes without the need for a database or permanent local storage, making it ideal for users who want to manage data through manual import/export cycles.

### 1.2 High-Level Objectives
* Provide a seamless, single-file user experience (HTML/CSS/JS).
* Facilitate easy data portability via JSON import/export.
* Offer a distraction-free, monospace-based editing environment.

---

## 2. Stakeholders & Personas
### 2.1 Primary Persona: The Transient Note-Taker
* **Profile:** A user who needs to organize thoughts or snippets of data during a single session or a specific task.
* **Needs:** A way to quickly create, view, and export notes without setting up an account or relying on a browser's long-term cache/local storage.
* **Pain Points:** Complexity of full-scale note apps; reliance on internet-based storage.

---

## 3. Functional Requirements

### 3.1 Note Management
* **FR-1: Note Creation:** The user shall be able to create a new note by clicking the "New" button located in the top application bar.
* **FR-2: Note Deletion:** The user shall be able to delete the currently active note by clicking the "Delete" button located in the right-hand pane's title bar.
* **FR-3: Deletion Confirmation:** The system shall present a standard browser confirmation dialog before finalizing the deletion of any note.
* **FR-4: Note Selection:** The user shall be able to select a note from an alphabetically sorted list of titles in the left-hand sidebar.
* **FR-5: Note Content Editing:** The user shall be able to edit the content of a note in the right-hand pane using a dedicated text area.
* **FR-6: Title Editing:** The user shall be able to edit the title of a note via a textbox in the right-hand pane's top bar.
* **FR-7: Real-Time Sidebar Update:** Upon losing focus (on blur) of the title textbox, the system shall automatically update the note title in the left-hand sidebar and re-sort the list alphabetically.
* **FR-8: Empty State:** When no note is selected, the right-hand workspace shall display as a blank area.

### 3.2 Data Portability (Import/Export)
* **FR-9: JSON Export:** The user shall be able to export all current session notes to a `.json` file via the "Export" button in the top bar.
* **FR-10: JSON Import:** The user shall be able to import notes from a `.json` file via the "Import" button in the top bar.
* **FR-11: Import Collision Logic:** During an import, the system shall check note titles. If a note title in the import file already exists in the current session, that specific note shall be skipped. All other unique notes shall be added to the list.
* **FR-12: Data Integrity:** The system shall validate the format of imported files. If the file is not a valid JSON or is improperly formatted, the system shall ignore the import and display a standard browser alert warning the user.

### 3.3 User Interface & Theme
* **FR-13: Theme Toggling:** The user shall be able to switch between "Light Mode" and "Dark Mode" via a toggle button in the top-right corner.
* **FR-14: Full-Page Theme Application:** The selected theme shall apply to the entire application interface, including the sidebar and the workspace.

---

## 4. Non-Functional Requirements

### 4.1 Usability
* **NFR-1: Visual Clarity:** The note content area shall use a **monospace font** to assist users who prefer a code-like or structured text environment.
* **NFR-2: UI Layout:** All input fields (Title and Content) shall automatically expand to utilize the available width and height of the workspace area.
* **NFR-3: Feedback Mechanism:** The system shall use standard browser alerts for all critical user interactions, including error messages, warnings, and deletions.

### 4.2 Portability & Architecture
* **NFR-4: Single-File Constraint:** The entire application (Structure, Styling, and Logic) must be contained within a single `.html` file.
* **NFR-5: Dependency Constraint:** The application shall not rely on any external libraries or CDNs (e.g., no jQuery, no FontAwesome, no Google Fonts). All assets must be embedded.

### 4.3 Reliability
* **NFR-6: Ephemeral Persistence:** The system shall not use `localStorage`. All data is transient and exists only for the duration of the current browser session unless manually exported.

---

## 5. Constraints & Assumptions
* **C-1: Desktop Focus:** The application is designed for desktop browser usage; responsiveness for mobile devices is not a requirement.
* **C-2: Browser Compatibility:** The application is intended for use in modern, "Evergreen" web browsers (e.g., latest versions of Chrome, Firefox, Safari, Edge).
* **C-3: User Responsibility:** Because the app does not use local storage, the user is responsible for manually exporting their data before closing the browser tab.

---

## 6. Glossary
* **JSON:** JavaScript Object Notation; the standard format for data interchange used for import/export.
* **Monospace Font:** A font where every character occupies the same amount of horizontal space.
* **Session:** The period from the time the HTML file is opened in a browser until the tab/window is closed.
* **Blur:** An event triggered when a user clicks away from an input field, losing focus on that element.
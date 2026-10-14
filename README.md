# Assignment 4 — Forms and Validation (HTML + Bootstrap)

**Student:** Azamat Bukharbayev  
**Group:** IT-2510  
**Course:** Web Development (Frontend)  
**Repository:** [https://github.com/azamatbukharbayev/Assignment4]

---

## Project Structure

```text
Assignment4_AzamatBukharbayev/
├── task1.html
├── task2.html
├── task3.html
├── css/
│   ├── task1.css
│   ├── task2.css
│   └── task3.css
├── README.md
├── Assignment4_AzamatBukharbayev.docx
└── Assignment4_AzamatBukharbayev.pdf
```

---

## Technical Overview

- **HTML5:** Semantic form controls, explicit label associations, native constraint validation (`min`, `max`, `step`, `minlength`, `maxlength`, `required`).
- **Bootstrap 5.3.3:** Form classes (`form-control`, `form-select`, `form-check`, `form-switch`, `form-floating`, `input-group`, `btn-group`, `btn-check`), grid system, and utility classes. Loaded via official CDN.
- **Custom CSS:** Strict color palette (`#0F6B5F`, `#F2A93B`, `#16302B`, `#F4F7F5`, `#E6EFEC`), Montserrat typography via Google Fonts, custom focus indicators, and interaction-aware validation via `:user-invalid` and `:user-valid` pseudo-classes.
- **Restrictions Enforced:** Zero JavaScript, zero `novalidate` attributes, zero `pattern` attributes, no fixed-width layouts, no absolute positioning.

---

## Testing and Verification Instructions

Each task is completely self-contained and runs directly in any modern browser (Chrome, Firefox, Safari, Edge).

### Task 1: Book a Train Ticket (`task1.html`)

1. Open `task1.html` in a web browser.
2. **Desktop View (1280 px):**
   - Verify centered card layout with teal `#0F6B5F` header bar.
   - Verify trip type toggle ("One way" / "Round trip") using styled radio buttons.
   - Verify floating labels for "From" and "To" fields.
   - Verify three-column row for Departure date, Return date, and Passengers select (1–6 adults).
   - Verify inline radio group for Carriage class (Seat, Coupé, Sleeper).
   - Verify input group for Phone with `+7` prefix badge, alongside Email field.
   - Verify SMS notification switch and carriage rules agreement checkbox.
   - Verify action buttons: "Clear" (outline) and "Find trains" (amber `#F2A93B` filled) aligned to the right.
3. **Mobile View (375 px):**
   - Open browser Developer Tools (F12 or Cmd+Option+I) and set device mode to 375 px width (e.g. iPhone SE).
   - Verify that all rows stack into a clean single column.
   - Verify that **"Find trains" appears directly ABOVE "Clear"** without changing HTML source order (implemented via `flex-direction: column-reverse`).
   - Verify both buttons expand to full width.
4. **Behavioral & Accessibility Verification:**
   - Attempt to submit with empty required fields; verify native browser constraint validation prompts appear.
   - Fill the form and click **Clear**; verify all controls reset to default state.
   - Navigate the entire form using keyboard only (`Tab`, `Shift+Tab`, `Space`, `Arrow keys`, `Enter`).

---

### Task 2: Registration for AITU Hack 2026 (`task2.html`)

1. Open `task2.html` in a web browser.
2. **Initial Load Check:**
   - Confirm that NO red borders or `.invalid-feedback` error messages are visible on initial page load.
3. **Interactive Validation Check:**
   - Click into each field, enter an invalid value, and tab out (blur/change).
   - Confirm that the red border and the specific `.invalid-feedback` message appear only after user interaction (governed by `:user-invalid`).
   - Enter a valid value; confirm the border turns green (`:user-valid`) and error feedback disappears.
4. **Verification Matrix:**

| Field | Rule | Must Accept | Must Reject | Verified Status |
| :--- | :--- | :--- | :--- | :--- |
| Full name * | 2–40 characters | `Anna-Maria Lee` | `A` | Pass |
| University email * | Valid email address | `a.fedenko@astanait.edu.kz` | `a.fedenko`, `a.fedenko@` | Pass |
| Age * | Whole number 16–30 | `18` | `15`, `31` | Pass |
| Team size * | Whole number 1–4 | `4` | `5`, `2.5` | Pass |
| Track * | Web, Mobile, AI, GameDev | `Web` | `Choose…` | Pass |
| Arrival day * | 20–22 November 2026 | `2026-11-21` | `2026-11-25` | Pass |
| Check-in time * | 09:00–18:00, step 30 min | `10:30` | `10:15`, `19:00` | Pass |
| Entry fee * | 0–5000 ₸, step 500 ₸ | `1500` | `1250`, `6000` | Pass |
| Experience level * | One of 3 radio buttons | `Beginner` | (nothing chosen) | Pass |
| GitHub profile | Optional full link | `(empty)`, `https://github.com/yerassyl-dev` | `github.com/yerassyl-dev` | Pass |
| Password * | 8–20 characters | `Astana2026` | `short` | Pass |
| Motivation * | 50–300 characters | 120 characters | 49 characters | Pass |
| Rules agreement * | Required checkbox | Ticked | Not ticked | Pass |

---

### Task 3: Fixed Café Reservation Form (`task3.html`)

1. Open `task3.html` in a web browser.
2. **Field Completeness Check:**
   - Verify that all original fields are retained: Name, Email, Phone, Guests, Date, Seating (Inside/Terrace), Meal (Lunch/Dinner), Comments, Terms checkbox, and Reserve button.
3. **Defect Rectification:**
   - All form controls are now programmatically paired with `<label for="...">`.
   - Semantic types used (`email`, `tel`, `number`, `date`, `radio`, `select`).
   - Duplicate `id="date"` eliminated (`id="date"` for date input, `id="seatingInside"` and `id="seatingTerrace"` for radios).
   - Seating radio buttons now share `name="seating"` to enforce mutual exclusivity.
   - Seating choices grouped in a semantic `<fieldset>` with `<legend>`.
   - Defective `<div class="btn btn-primary">` replaced with native `<button type="submit" class="btn btn-reserve w-100">`.
4. **W3C Validation Check:**
   - Open [https://validator.w3.org/nu/](https://validator.w3.org/nu/)
   - Upload or paste `task3.html`
   - Verify: **Document checking completed. No errors or warnings to show.**

# Income/Expense Tracker (Vanilla JS)

A simple, single-page web app to record income transactions and view them in a table. Built with plain HTML, CSS, and JavaScript. No build step or backend required.

Note: The UI currently labels the app as "Income Tracker" while the folder is named "Expense Tracker". Functionality is the same for basic transaction tracking; you can rename labels to suit your needs.

## Features
- Add transactions with amount, type, and optional description
- Auto-formatted currency display using Indian Rupee (₹)
- Responsive, clean UI with table-based history
- In-memory data storage for demo simplicity (resets on refresh)

## Quick Start
1. Download or clone the repository.
2. Open `expense_tracker.html` directly in any modern browser.
   - Optionally serve via a local web server:
     - Python 3: `python -m http.server 8000`
     - Node (http-server): `npx http-server -p 8000`
3. Interact with the form to add transactions; the table will update instantly.

## Usage
- Amount: Enter a non-negative number.
- Type of Income: Short text label such as Salary, Freelance, Investment.
- Description: Optional notes.
- Click "Add Transaction" to append the entry to the history table.

Data is kept only in memory (`window.userData`) to simplify the demo. Reloading the page clears the table. See "Persisting Data" below to store entries.

## Project Structure
```
.
├─ expense_tracker.html  # Single page app (HTML + CSS + JS)
└─ README.md
```

## Tech Stack
- HTML5 for structure
- CSS3 for styling
- Vanilla JavaScript for form handling and rendering

## How It Works
- Form submit is intercepted with `onsubmit="generate(event)"`.
- New entries are appended to an array on `window.userData`.
- The history table is rendered by `showHistory()` using the current array contents.
- Amounts are displayed as ₹ with `toLocaleString()` formatting.

## Persisting Data (Optional)
To keep entries across reloads, replace the in-memory array with `localStorage`:

```js
// On read
const data = JSON.parse(localStorage.getItem('userData') || '[]');

// On write
localStorage.setItem('userData', JSON.stringify(data));
```

You would:
- Initialize `window.userData` from `localStorage` on load.
- Update `localStorage` whenever a new entry is added.

## Roadmap Ideas
- Add delete and edit actions per transaction
- Track expenses vs income and compute totals/balance
- Categories, filters, and search
- LocalStorage persistence by default
- Export/import to CSV/JSON
- Basic validation messages and inline errors
- Accessibility improvements and keyboard shortcuts

## License
MIT

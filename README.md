# Expense Tape

A single-file running-tape expense calculator for keeping BDT and USD expenses separate.

## Live demo

[Open Expense Tape](https://iamggd.github.io/expense-tape/)

## Screenshots

### Empty Expense Tape interface

![Empty Expense Tape interface](docs/screenshots/empty-interface.png)

### Five USD entries totaling $15.00

![Expense Tape with five USD entries totaling $15.00](docs/screenshots/five-usd-entries-total-15.png)

### Generated PDF export

![Generated Expense Tape PDF export](docs/screenshots/generated-pdf-export.png)

## Features

- Enter an amount in BDT (৳) or USD ($).
- Add an optional note to each expense.
- View live totals for BDT and USD separately. Amounts are never mixed or converted.
- View the live number of entries.
- Display a final result with the total for each currency and the number of entries counted.
- Delete individual entries or clear all entries.
- Export an itemised PDF containing:
  - Serial number
  - Note
  - Currency
  - Amount
  - Running total
  - Final totals and entry count
- Automatically add page breaks when the exported PDF spans multiple pages.
- Save entries in the browser using `localStorage`.

## Getting started

### Run locally

1. Download or clone this repository.
2. Open `index.html` in a modern web browser.
3. Select a currency, enter an amount, optionally add a note, and select **+ Add**.

No build step, backend, package manager, or server is required for local use.

### Deploy on GitHub Pages

1. Push `index.html` and `README.md` to a GitHub repository.
2. Open the repository's **Settings**.
3. Select **Pages** under **Code and automation**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select the branch containing `index.html` and the `/ (root)` folder, then save.
6. After GitHub Pages finishes deploying, verify the live demo URL above matches the repository's Pages URL.

## How it works

Expense Tape is implemented entirely in `index.html` using HTML, CSS, and vanilla JavaScript. Entries are stored in an array and persisted to browser `localStorage`. BDT and USD totals are calculated independently.

Amounts are stored as integer minor units—paisa for BDT and cents for USD—by multiplying the entered value by 100 and rounding it. This avoids common floating-point calculation errors. Display values are formatted with two decimal places.

PDF export uses jsPDF 2.5.1 loaded from cdnjs. The export builds a table with running totals for each currency and adds a new page when needed.

## Limitations

- Non-Latin characters, such as Bengali text in notes, are replaced with `?` in exported PDFs because jsPDF's default font is Latin-only. They display correctly in the app.
- PDF export requires an internet connection to load jsPDF from the CDN.
- Data is stored in one browser on one device using `localStorage`; there is no synchronisation.
- BDT and USD are not converted into one another.

## Possible future improvements

- Embed a Bengali-compatible font for PDF export.
- Add currency conversion using a user-selected exchange rate or an exchange-rate service.
- Bundle or cache jsPDF so PDF export can work offline.

# Gather — Event Discovery & Registration

A responsive event management website built with semantic HTML5, CSS3, and vanilla JavaScript. No build step or framework required.

## Run locally

From this directory, run `python3 -m http.server 8000 --directory dist` and open http://localhost:8000. You can also open `dist/index.html` directly, although browser storage behavior may vary on file URLs.

## Features

- Six curated fictional events with images, dates, venues, descriptions, prices and hosts
- Live text search, category filters, saved-events filter and three sorting options
- Event details in accessible native dialogs and countdown timers
- Registration form with name, email and telephone validation
- Confirmation codes, duplicate registration prevention, My Tickets, cancellation, calendar export
- Local Storage for registrations, saved events and theme preference, with graceful session fallback
- Responsive layouts, dark/light mode, scroll reveals, hover transitions and reduced-motion support
- Keyboard navigation, search shortcut (/), dialog Escape support and clear form errors

## Project structure

- `dist/index.html` — semantic page structure and dialogs
- `dist/styles.css` — visual design, responsive layouts and animations
- `dist/app.js` — event data, discovery, validation, storage and ticket interactions
- `.openai/hosting.json` — static hosting configuration

## Demo scope & privacy

All events are fictional sample content. Registrations are stored only in the visitor's browser; no real reservations, payments, emails or SMS are processed. Do not enter sensitive information on shared devices. Use **Privacy & storage → Delete my local data** to clear this app's stored records. No backend is required. Google Fonts and Unsplash images require an internet connection; system fonts provide a fallback.

Dates are displayed in Indian Standard Time. Edit the `events` array in `dist/app.js` to change event content, dates, venues, prices or image URLs.

## Submission

Source repository: https://github.com/dokja-5149/website

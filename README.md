# Gather — Event Management Website

Gather is a responsive event discovery and registration website built as a student project. Visitors can explore upcoming experiences, read event details, and register through an interactive, validated form.

## Technology stack

- **HTML5:** semantic page structure, forms, navigation, and native `<dialog>` elements.
- **CSS3:** custom properties, Grid, Flexbox, responsive media queries, transitions, and keyframe animations.
- **JavaScript:** DOM rendering, event handling, validation, countdowns, calendar export, and browser storage.
- **Git and GitHub:** source version control and project submission.

No framework, package installation, or build step is required.

## Run locally

### Option 1: Local server (recommended)

Install Python 3, clone the repository, and run:

```bash
git clone https://github.com/dokja-5149/website.git
cd website
python3 -m http.server 8000 --directory dist
```

On Windows, use `python` or `py` instead of `python3` if needed.

Open **http://localhost:8000** in a modern browser. Stop the server with **Ctrl+C**.

### Option 2: Open directly

Open `dist/index.html` in a browser. Browser storage behavior can vary with file URLs, so a local server is recommended.

## Features

- Hero section and six curated sample events with images, dates, venues, descriptions, and prices.
- Featured event badges, live search, category filtering, and sorting.
- Saved-event bookmarks and a saved-only filter.
- Event details with schedules, hosts, expectations, prices, and countdown timers.
- Registration with full name, email address, phone number, and event selection.
- Field-specific JavaScript validation and a successful-registration confirmation.
- Unique demo ticket codes, My Tickets, duplicate-event registration prevention, and cancellation.
- Downloadable calendar entries in `.ics` format.
- Dark/light theme with a persistent preference.
- Scroll reveals, image zoom, animated ticker, floating accent, dialog transitions, and button interactions.
- Responsive layouts for phones, tablets, and desktops.
- Reduced-motion support, keyboard focus indicators, Escape-to-close dialogs, and a `/` search shortcut.

## Project structure

```text
website/
├── README.md
└── dist/
    ├── index.html
    ├── styles.css
    └── app.js
```

| File | Purpose |
| --- | --- |
| `dist/index.html` | Semantic sections, navigation, search controls, event grid, dialogs, and footer. |
| `dist/styles.css` | Theme variables, typography, layout, responsive breakpoints, and animation rules. |
| `dist/app.js` | Sample event data, rendering, filters, forms, storage, tickets, and calendar downloads. |

## Implementation

### Event data and rendering

An `events` array in `app.js` defines each event's identifier, title, category, dates, venue, city, price, image, host, and descriptive content. The `renderEvents()` function builds cards from this data.

Search matches titles, categories, venues, cities, and descriptions. Search, category selection, and the saved-only filter work together. Results can be ordered by date, featured status, or price. An empty state provides a reset button when nothing matches.

### Event details

Selecting an event opens a native modal dialog. `openDetails()` renders its full information, while `updateCountdown()` displays the remaining days, hours, and minutes. Countdown updates run once per minute.

Dates and times are formatted using `Intl.DateTimeFormat` in **Indian Standard Time (Asia/Kolkata)**. Registration is blocked once an event's start time has passed.

### Registration validation

`openRegistration()` creates the registration form, and `submitRegistration()` validates it before saving:

| Field | Validation |
| --- | --- |
| Full name | At least two characters after trimming; must contain a Unicode letter. |
| Email | Browser email validity plus a basic email-pattern check. |
| Phone | Optional leading plus, supported formatting characters, 10–15 digits, and rejection of repeated identical digits. |
| Event | Must identify an existing event whose registration is still open. |

Errors appear next to the relevant inputs, invalid fields receive `aria-invalid`, and focus moves to the first invalid input. A second registration for the same event on the current browser is prevented.

A successful submission creates a ticket code using `crypto.getRandomValues()`, stores the registration, and displays confirmation. User-entered text is escaped before insertion into generated HTML.

### Local Storage

The application stores JSON under these keys:

| Key | Stored value |
| --- | --- |
| `gather-tickets` | Participant details, event identifiers, ticket codes, and creation timestamps. |
| `gather-saved` | Saved event identifiers. |
| `gather-theme` | Light or dark preference. |

Storage reads handle invalid JSON, and writes handle unavailable storage. If persistence fails, the current session remains usable and a message explains the limitation. **Privacy & storage → Delete my local data** removes the application's stored records.

### Tickets and calendar export

My Tickets displays registrations saved in the current browser. Visitors can cancel a registration or download an iCalendar file. Calendar exports use UTC timestamps and label the experience as a demo event.

### Styling, responsiveness, and animation

The design uses a warm ivory background, lime accents, large typography, and event photography. CSS variables define the light and dark palettes.

Grid and Flexbox organize the layout. Media queries adapt navigation, hero content, cards, and dialogs to smaller screens, including narrow phones. Keyframes and transitions provide motion; `prefers-reduced-motion` disables animations and smooth scrolling for visitors who request less motion.

## Manual verification

Checks performed during implementation:

- JavaScript syntax check with `node --check dist/app.js`.
- Event detail dialog and registration navigation.
- Empty-form validation messages.
- Successful registration and ticket confirmation.
- Ticket persistence after page reload.
- Text search, category filters, and saved-event filtering.
- Dark/light theme switching.

Additional recommended submission checks: open the website at mobile and tablet widths, try invalid email and phone values, cancel a test ticket, and import a downloaded calendar file.

## Customization

Edit the `events` array in `dist/app.js` to change event content, images, prices, venues, or schedules. Dates use ISO 8601 timestamps with an explicit time-zone offset.

Edit the variables at the beginning of `dist/styles.css` to change the color palette. Replace the logo text, hero copy, and introductory sections in `dist/index.html` to change the branding.

## Demo scope and limitations

All events are fictional sample content. Registrations are stored only in the visitor's browser; no data is sent to event organizers. This project does not process payments, create real reservations, send email/SMS, or synchronize tickets across devices.

Local Storage is not a secure production database. Avoid entering sensitive information on shared devices. A production implementation would require a backend, server-side validation, persistent database storage, authentication as appropriate, and real booking/email integrations.

Google Fonts and Unsplash images require internet access. System fonts provide a fallback.

## Credits

- Typography: DM Sans and Manrope via Google Fonts.
- Photography: Unsplash.
- Implementation: HTML5, CSS3, and vanilla JavaScript.

## Links

- Repository: https://github.com/dokja-5149/website

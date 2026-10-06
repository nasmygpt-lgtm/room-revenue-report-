# 🏨 Room Availability Dashboard

A single-page, self-contained HTML dashboard for hotel revenue and front-office teams. Visualize room availability, occupancy rates, and suggested pricing — all from a PMS screenshot or manual data entry.

![Dashboard Preview](https://img.shields.io/badge/Status-Ready-brightgreen) ![HTML](https://img.shields.io/badge/Tech-HTML%2FCSS%2FJS-blue) ![No Dependencies](https://img.shields.io/badge/Dependencies-None-lightgrey)

## ✨ Features

### 📸 Screenshot → Data (automatic OCR)
Paste a PMS "Detailed Availability" screenshot and the dashboard **reads it automatically** using in-browser OCR (Tesseract.js) — it extracts the Date column and the first numeric "Total" (Available) column. No typing required.

Four ways to give it the screenshot:
1. **Click-to-upload** file picker
2. **Drag & drop** onto the upload zone
3. **Ctrl+V paste** anywhere on the page
4. **Clipboard button** (`navigator.clipboard.read`)

A **manual entry** box is available as a backup only (for blurry or unavailable screenshots).

> **Tip:** A tight, zoomed-in crop of just the Date + Total columns gives the most accurate OCR results.

### 📊 Occupancy Chart
- CSS-only stacked bar chart (no external libraries)
- Color-coded: 🟢 <30% | 🟡 30–70% | 🔴 ≥70% occupancy
- Shows suggested rate, occupancy %, and booked count per date
- Weekends highlighted in amber

### 💰 Rate Suggestions (AED)
Priority-based pricing tiers:

| Condition | Rate |
|-----------|------|
| <10 rooms left | 250+15 |
| <20 rooms left | 225+15 |
| <30 rooms left | 185+15 RO |
| ≥70% occupancy | 160+15 Walk-in |
| 50–70% | 135+15 RO |
| 40–50% | 125+15 |
| <40% | 115+15 |

### 🔴 70% Trigger Rate Card
When occupancy hits the trigger threshold:
- Walk-in: AED 160+15
- Online (Direct): AED 190++
- NRF: AED 171++
- Agoda RO: AED 150–160
- Agoda BB: AED 185

### 📈 KPI Cards
- Average occupancy
- Fullest / emptiest dates
- Total unsold room-nights

### 💡 Auto-Generated Insights
- Dates above trigger threshold
- Weakest dates needing attention
- Weekend vs weekday comparison
- Revenue opportunity from unsold inventory

### 📅 Day-wise Table
- Editable "Available" values (everything recalculates live)
- Booked, Occupancy %, Suggested Rate, Status, Rooms to Trigger, Rate Mode

## 🚀 Usage

1. Open `index.html` in any modern browser
2. The dashboard loads with **prefilled sample data** (14 days starting 06/10/2026)
3. Upload a PMS screenshot or enter data manually
4. Adjust **Total Rooms** (default: 140) and **Trigger %** (default: 70%)
5. Edit any Available value in the table — all calculations update instantly

## ⚙️ Configuration

| Setting | Default | Description |
|---------|---------|-------------|
| Total Rooms | 140 | Total number of rooms in the hotel |
| Trigger % | 70 | Occupancy threshold for rate card activation |

## 🎨 Themes

- **Light mode** (default)
- **Dark mode** — toggle with the 🌙/☀️ button
- Auto-detects system preference

## 📱 Responsive

Fully responsive design — works on desktop, tablet, and mobile devices.

## 🔧 Technical

- **Single HTML file** with inline CSS & JS
- **One external dependency:** [Tesseract.js](https://github.com/naptha/tesseract.js) (loaded from jsDelivr CDN) for real in-browser OCR — this is what makes the paste-a-screenshot feature actually work
- **No API keys, no backend** — OCR runs entirely in your browser
- **No localStorage** — fresh state on every load
- **Mobile-friendly** with `viewport-fit=cover`
- **Requires internet** on first use so the OCR engine (and its English language data) can download

## 📄 License

MIT

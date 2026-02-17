# 🕷️ ScrapeFlow — Web Scraper & Data Pipeline Dashboard

A real-time web scraper dashboard with live progress tracking, log streaming, data table output, and CSV/JSON export. Built to demonstrate automation pipeline UX.

## 🚀 Features

- **Configurable Scraper** — Set URL, data type, CSS selectors, max pages, headless mode, proxy rotation, deduplication
- **Job Queue Manager** — View and switch between multiple concurrent scraping jobs
- **Live Progress Bar** — Real-time progress %, pages scraped, items extracted, error count, speed
- **Streaming Log Console** — Terminal-style log with color-coded levels (info, success, warn, error, data)
- **Scraped Data Table** — Paginated, scrollable table with priority tags
- **Export Options** — CSV download, JSON download, webhook push

## 🛠 Tech Stack

- Single-file HTML/CSS/JS — zero dependencies
- Canvas-free progress visualization
- Simulated async scraping pipeline with setInterval
- Real CSV/JSON blob download via `URL.createObjectURL`

## 📂 File Structure

```
02-web-scraper-dashboard/
├── index.html    # Complete application
└── README.md     # This file
```

## 🏃 Quick Start

```bash
open index.html
# or
npx serve .
```

## 💡 How to Demo

1. Enter any URL in the form (e.g. `https://amazon.com`)
2. Select data type: Products, Leads, News, Jobs, or Reviews
3. Click **▶ Start Scraping**
4. Watch the live log, progress bar, and data table populate
5. Click **CSV** or **JSON** to download the extracted data

## 🔌 Production Integration

```python
# Real scraper backend with Playwright
from playwright.async_api import async_playwright
import asyncio, json

async def scrape(url, selector):
    async with async_playwright() as p:
        browser = await p.chromium.launch(headless=True)
        page = await browser.new_page()
        await page.goto(url)
        items = await page.query_selector_all(selector)
        data = [await el.inner_text() for el in items]
        await browser.close()
        return data

# Send progress to frontend via WebSocket
# ws.send(json.dumps({"progress": 45, "items": 312}))
```

## 🏗️ Architecture

```
Frontend (this) ←→ WebSocket ←→ Scraper Backend
                                    ↓
                              Proxy Pool
                                    ↓
                              Data Pipeline
                                    ↓
                          Database / Webhook
```

## 📝 License

MIT

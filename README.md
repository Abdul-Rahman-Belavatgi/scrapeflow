🕷️ ScrapeFlow — Web Scraper & Data Pipeline Dashboard

> Real-time web scraper dashboard with live progress, streaming logs, and CSV/JSON export.

![License](https://img.shields.io/badge/license-MIT-blue) ![Vanilla JS](https://img.shields.io/badge/vanilla-JS-yellow) ![Zero Deps](https://img.shields.io/badge/dependencies-zero-brightgreen)

## 🚀 Quick Start
```bash
git clone https://github.com/YOUR_USERNAME/scrapeflow
open index.html
```

## ✨ Features
- Configure URL, data type, CSS selectors, max pages, headless mode, proxy rotation
- Live progress bar with pages scraped, items found, errors, and speed
- Terminal-style streaming log with color-coded levels (info / success / warn / error)
- Scraped data table with real CSV and JSON download
- Multi-job queue manager with status tracking

## 🔌 Real Backend (Python + Playwright)
```python
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
```

## 📝 License
MIT
EOF

git init
git add .
git commit -m "Initial commit — ScrapeFlow Web Scraper Dashboard"
gh repo create scrapeflow --public --source=. --push

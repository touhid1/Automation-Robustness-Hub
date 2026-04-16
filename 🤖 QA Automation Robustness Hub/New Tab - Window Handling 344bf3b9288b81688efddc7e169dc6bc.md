# New Tab - Window Handling

Category: Browser Features, Navigation
Difficulty: Medium
Framework: Cypress, Playwright, Selenium
Priority: 6
Status: Not Started

## Challenge: New Tab - Window Handling

### বিবরণ | Description

বোতাম click করে নতুন tab open করুন এবং opened page এর text assert করুন।

Open new tab by clicking on the button and assert text on the opened new page.

### সেরা অনুশীলন | Best Practices

- ✅ waitForEvent('popup') ব্যবহার করুন নতুন pages এর জন্য
- ✅ Multiple pages/contexts handle করুন properly
- ✅ Page loading complete হওয়া পর্যন্ত wait করুন
- ✅ Original page এ রেফারেন্স রাখুন

### সাধারণ সমস্যা | Common Pitfalls

❌ নতুন page open হওয়া পর্যন্ত wait না করা

❌ Wrong page context এ assertion করা

❌ New page loading complete না হওয়া পর্যন্ত access করা

### সমাধান কোড | Solution Code

```jsx
// Playwright
await page.goto('https://qaplayground.dev/apps/new-tab/');
const newPagePromise = context.waitForEvent('page');
await page.locator('button:has-text("Open New Tab")').click();
const newPage = await newPagePromise;
await newPage.waitForLoadState('networkidle');

const heading = await newPage.locator('h1').textContent();
expect(heading).toBe('New Page');
await newPage.close();
```
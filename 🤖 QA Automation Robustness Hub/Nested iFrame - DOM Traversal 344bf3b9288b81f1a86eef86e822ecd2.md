# Nested iFrame - DOM Traversal

Category: Browser Features, DOM Handling
Difficulty: Hard
Framework: Cypress, Playwright, Selenium
Priority: 8
Status: Not Started

## Challenge: Nested Iframe - DOM Traversal

### বিবরণ | Description

একটি iframe এর ভিতরে থাকা আরেকটি iframe এর ভিতরে button click করুন এবং success message assert করুন।

Click on the button in the iframe that is in another iframe and assert a success message.

### সেরা অনুশীলন | Best Practices

- ✅ frameLocator() ব্যবহার করুন ক্রমানুসারে nested iframes access করতে
- ✅ প্রতিটি iframe level এ load wait করুন
- ✅ Inner iframe এর content properly select করুন
- ✅ Cross-origin issues handle করুন carefully

### সাধারণ সমস্যা | Common Pitfalls

❌ iFrame load না হওয়া পর্যন্ত access করা

❌ নেস্টিং level skip করা

❌ Cross-origin iFrame এ direct access attempt করা

### সমাধান কোড | Solution Code

```jsx
// Playwright
await page.goto('https://qaplayground.dev/apps/iframe/');
const frameOne = page.frameLocator('iframe[name="outer"]');
const frameTwo = frameOne.frameLocator('iframe[name="inner"]');

await frameTwo.locator('button').click();
const message = await frameTwo.locator('.success').textContent();
expect(message).toContain('Success');
```
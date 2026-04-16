# Fetching Data - API & Wait Conditions

Category: API Testing, Dynamic Content
Difficulty: Medium
Framework: Cypress, Playwright, Selenium
Priority: 12
Status: Not Started

## Challenge: Fetching Data - API & Wait Conditions

### বিবরণ | Description

API ডেটা fetch হওয়া পর্যন্ত wait করুন এবং তারপর loaded posts assert করুন।

Wait until API data is fetched and then assert loaded posts.

### সেরা অনুশীলন | Best Practices

- ✅ waitForLoadState('networkidle') ব্যবহার করুন API calls complete করতে
- ✅ waitForSelector() ব্যবহার করুন loading finished হওয়ার জন্য
- ✅ Network requests intercept করুন যদি প্রয়োজন
- ✅ Explicit waits use করুন implicit এর জন্য prefer করুন

### সাধারণ সমস্যা | Common Pitfalls

❌ Hard-coded delays ব্যবহার করা

❌ Network request monitoring না করা

❌ API failure cases handle না করা

### সমাধান কোড | Solution Code

```jsx
// Playwright
await page.goto('https://qaplayground.dev/apps/fetch/');
await page.waitForLoadState('networkidle');

const posts = await page.$$('.post-item');
expect(posts.length).toBeGreaterThan(0);

const firstPost = await page.locator('.post-item:first-child h2').textContent();
expect(firstPost).toBeTruthy();

// Or intercept API
await page.on('response', response => {
  if (response.url().includes('/api/posts')) {
    expect(response.status()).toBe(200);
  }
});
```
# Geolocation - Browser API

Category: Browser Features
Difficulty: Medium
Framework: Playwright, Selenium
Priority: 11
Status: Not Started

## Challenge: Geolocation - Browser API

### বিবরণ | Description

ব্রাউজার geolocation সেট করুন longitude: -122.03118 এবং latitude: 37.33182 এবং Cupertino assert করুন।

Set browser geolocation to longitude: -122.03118 and latitude: 37.33182 and assert Cupertino.

### সেরা অনুশীলন | Best Practices

- ✅ grantPermissions() ব্যবহার করুন geolocation permission দিতে
- ✅ setGeolocation() accurate coordinates দিয়ে call করুন
- ✅ Page দ্বারা geolocation access করার জন্য wait করুন
- ✅ Returned location name verify করুন

### সাধারণ সমস্যা | Common Pitfalls

❌ Permission grant না করে geolocation set করা

❌ Incorrect coordinate format ব্যবহার করা

❌ Reverse geocoding API না wait করা

### সমাধান কোড | Solution Code

```jsx
// Playwright
const context = await browser.newContext({
  geolocation: { longitude: -122.03118, latitude: 37.33182 },
  permissions: ['geolocation']
});
const page = await context.newPage();

await page.goto('https://qaplayground.dev/apps/geolocation/');
const location = await page.locator('.location-name').textContent();
expect(location).toContain('Cupertino');
```
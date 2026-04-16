# Shadow DOM - Encapsulation

Category: Browser Features, DOM Handling
Difficulty: Hard
Framework: Cypress, Playwright
Priority: 9
Status: Not Started

## Challenge: Shadow DOM - Encapsulation

### বিবরণ | Description

Shadow DOM এর ভিতরে button click করুন এবং progress 95% এ আছে তা assert করুন।

Click on the button and assert that progress is on the 95 percent.

### সেরা অনুশীলন | Best Practices

- ✅ pierce combinator ব্যবহার করুন Shadow DOM penetrate করতে
- ✅ Custom element selectors properly craft করুন
- ✅ JavaScript execution ব্যবহার করুন Shadow DOM access করতে যদি প্রয়োজন
- ✅ Progress element state verify করুন

### সাধারণ সমস্যা | Common Pitfalls

❌ Shadow DOM elements directly select করার চেষ্টা করা

❌ pierce combinator ছাড়াই nested selectors use করা

❌ Browser DevTools এ visible কিন্তু selector fail করা

### সমাধান কোড | Solution Code

```jsx
// Playwright
await page.goto('https://qaplayground.dev/apps/shadow-dom/');
const button = page.locator('custom-element >>> button');
await button.click();

const progress = await page.evaluate(() => {
  const element = document.querySelector('custom-element');
  return element.shadowRoot.querySelector('.progress').value;
});
expect(progress).toBe(95);
```
# Sortable List - Drag & Drop

Category: DOM Handling, Interactions
Difficulty: Hard
Framework: Cypress, Playwright
Priority: 5
Status: Not Started

## Challenge: Sortable List - Drag & Drop

### বিবরণ | Description

লিস্ট আইটেম drag এবং drop করে সঠিক ক্রমে সাজান। সব items green text পাওয়ার পরে button click করুন।

Drag and drop list items to make the correct order and then click on the button and assert that all have green text.

### সেরা অনুশীলন | Best Practices

- ✅ dragTo() বা drag-drop actions সঠিকভাবে use করুন
- ✅ Animation complete হওয়া পর্যন্ত wait করুন
- ✅ Item positions verify করুন sorting এর পরে
- ✅ Visual indicators (color) check করুন

### সাধারণ সমস্যা | Common Pitfalls

❌ Drop animation complete না হওয়া পর্যন্ত assertion করা

❌ Parent list এর বদলে item select করা

❌ Browser support issues drag/drop এর জন্য

### সমাধান কোড | Solution Code

```jsx
// Playwright
await page.goto('https://qaplayground.dev/apps/sortable-list/');
const items = await page.$$('.sortable-item');

// Drag items to correct order
const firstItem = page.locator('.sortable-item:first-child');
const lastItem = page.locator('.sortable-item:last-child');
await firstItem.dragTo(lastItem);

await page.waitForLoadState('networkidle');
await page.locator('button').click();

const allGreen = await page.$$eval('.sortable-item', items => 
  items.every(i => window.getComputedStyle(i).color === 'green')
);
expect(allGreen).toBe(true);
```
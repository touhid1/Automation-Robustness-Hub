# Dynamic Table - Find Spider-Man

Category: DOM Handling, Interactions
Difficulty: Medium
Framework: Cypress, Playwright, Selenium
Priority: 1
Status: Not Started

## Challenge: Dynamic Table - Find Spider-Man

### বিবরণ | Description

একটি টেবিল থেকে স্পাইডার-ম্যান খুঁজুন যেখানে সারিগুলি ক্রমাগত পরিবর্তিত হয়। আসল নাম নিশ্চিত করুন।

Find Spider-Man in a table that changes the order of rows and assert his real name.

### সেরা অনুশীলন | Best Practices

- ✅ Dynamic selectors ব্যবহার করুন স্থির indexing এর পরিবর্তে
- ✅ Table পড়ার জন্য explicit waits ব্যবহার করুন
- ✅ Text search करने জন্য contains() selector ব্যবহার করুন
- ✅ Column values ডায়নামিক্যালি বের করুন

### সাধারণ সমস্যা | Common Pitfalls

❌ Hard-coded row indices ব্যবহার করা

❌ Table data load হওয়ার আগে assertion করা

❌ Exact match এ নির্ভর করা যখন partial match যথেষ্ট

### সমাধান কোড | Solution Code

```jsx
// Playwright Example
await page.goto('https://qaplayground.dev/apps/dynamic-table/');
await page.waitForSelector('table tbody tr');
const rows = await page.$$('table tbody tr');

for (const row of rows) {
  const cells = await row.$$('td');
  if (cells.length > 0) {
    const heroName = await cells[0].textContent();
    if (heroName.includes('Spider-Man')) {
      const realName = await cells[1].textContent();
      expect(realName).toBe('Peter Parker');
      break;
    }
  }
}
```
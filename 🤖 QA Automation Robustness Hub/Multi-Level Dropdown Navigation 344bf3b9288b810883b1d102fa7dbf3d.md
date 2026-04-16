# Multi-Level Dropdown Navigation

Category: Interactions, Navigation
Difficulty: Medium
Framework: Cypress, Playwright
Priority: 4
Status: Not Started

## Challenge: Multi-Level Dropdown Navigation

### বিবরণ | Description

সাব-মেনুতে navigate করুন এবং মেনু আইটেম text এবং links যাচাই করুন।

Navigate into the sub-menus and assert menu items text and link.

### সেরা অনুশীলন | Best Practices

- ✅ Hover actions properly sequence করুন
- ✅ Nested menu visibility wait করুন
- ✅ Link targets verify করুন
- ✅ Mouse leave/enter events handle করুন

### সাধারণ সমস্যা | Common Pitfalls

❌ Hover transitions complete না হওয়া পর্যন্ত wait না করা

❌ Submenu selector parent menu select করা

❌ Multiple menu levels traverse না করা

### সমাধান কোড | Solution Code

```jsx
// Playwright
await page.goto('https://qaplayground.dev/apps/multi-level-dropdown/');
const menu = page.locator('nav > ul > li:has-text("Products")');
await menu.hover();
const submenu = page.locator('nav >> text=Premium');
await submenu.waitFor({ state: 'visible' });
await submenu.click();
const heading = await page.locator('h1').textContent();
expect(heading).toContain('Premium');
```
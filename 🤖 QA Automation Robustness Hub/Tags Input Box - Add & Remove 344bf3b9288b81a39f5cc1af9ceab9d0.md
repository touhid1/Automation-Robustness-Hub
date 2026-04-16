# Tags Input Box - Add & Remove

Category: Form Elements, Interactions
Difficulty: Medium
Framework: Cypress, Playwright, Selenium
Priority: 3
Status: Not Started

## Challenge: Tags Input Box - Add & Remove

### বিবরণ | Description

ট্যাগ যোগ এবং সরিয়ে ফেলুন। ট্যাগের উপস্থিতি এবং সংখ্যা যাচাই করুন।

Add and remove tags and assert tag's presence and count.

### সেরা অনুশীলন | Best Practices

- ✅ Dynamic tag list handle করুন
- ✅ Remove button locators বিশেষভাবে target করুন
- ✅ DOM mutations observe করুন
- ✅ Tag count dynamically verify করুন

### সাধারণ সমস্যা | Common Pitfalls

❌ Static selectors remove buttons এর জন্য

❌ Tag added না হওয়া পর্যন্ত wait না করা

❌ Previous state থেকে selector reuse করা

### সমাধান কোড | Solution Code

```jsx
// Cypress
cy.visit('https://qaplayground.dev/apps/tags-input-box/');
cy.get('input[placeholder="Enter tags"]').type('JavaScript{enter}');
cy.get('input[placeholder="Enter tags"]').type('Testing{enter}');

cy.get('.tag').should('have.length', 2);
cy.contains('.tag', 'JavaScript').should('be.visible');
cy.contains('.tag', 'JavaScript').find('.remove-btn').click();
cy.get('.tag').should('have.length', 1);
```
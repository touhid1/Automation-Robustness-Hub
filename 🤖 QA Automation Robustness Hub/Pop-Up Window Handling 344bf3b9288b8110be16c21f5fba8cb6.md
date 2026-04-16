# Pop-Up Window Handling

Category: Browser Features, Interactions
Difficulty: Medium
Framework: Cypress, Playwright, Selenium
Priority: 7
Status: Not Started

## Challenge: Pop-Up Window Handling

### বিবরণ | Description

পপ-আপ খুলুন, এতে button click করুন এবং main window এ text assert করুন।

Open pop-up and click on the button in it and assert text on the main window.

### সেরা অনুশীলন | Best Practices

- ✅ Pop-up visibility wait করুন DOM এ পরিবর্তনের আগে
- ✅ Pop-up context access করুন সঠিকভাবে
- ✅ Pop-up এর button interact করুন
- ✅ Main window এর changes verify করুন

### সাধারণ সমস্যা | Common Pitfalls

❌ Pop-up render না হওয়া পর্যন্ত interact করা

❌ Wrong iframe/context এ interact করা

❌ Original window reference হারানো

### সমাধান কোড | Solution Code

```jsx
// Cypress
cy.visit('https://qaplayground.dev/apps/popup/');
cy.get('button:contains("Open Popup")').click();
cy.get('.popup').should('be.visible');
cy.get('.popup button').click();
cy.get('.popup').should('not.exist');
cy.get('.result-text').should('contain', 'Popup was clicked');
```
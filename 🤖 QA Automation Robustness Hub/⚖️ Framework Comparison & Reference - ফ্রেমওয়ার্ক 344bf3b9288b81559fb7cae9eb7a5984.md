# ⚖️ Framework Comparison & Reference - ফ্রেমওয়ার্ক তুলনা ও রেফারেন্স

# Framework Comparison & Quick Reference

# ফ্রেমওয়ার্ক তুলনা ও দ্রুত রেফারেন্স

## 🎯 Framework Selection Guide | ফ্রেমওয়ার্ক নির্বাচন গাইড

### Playwright ⚡

**Pros | সুবিধা:**

- ✅ Fastest execution
- ✅ Best API design
- ✅ Cross-browser out of the box
- ✅ Great documentation
- ✅ Network interception
- ✅ Shadow DOM support

**Cons | অসুবিধা:**

- ❌ Newer framework (less community resources)
- ❌ Steeper learning curve for beginners

**Best For | সেরা ব্যবহার:**

- Modern web applications
- API testing combined with UI
- Performance-critical tests

**Installation | ইনস্টলেশন:**

```bash
npm init playwright@latest
cd playwright-example
npm install
```

---

### Cypress 🌳

**Pros | সুবিধা:**

- ✅ Excellent debugging experience
- ✅ Time-traveling debugger
- ✅ Great for beginners
- ✅ Strong community
- ✅ Good documentation
- ✅ Open-source

**Cons | অসুবিধা:**

- ❌ Slower than Playwright
- ❌ Only Chrome/Edge/Firefox (limited browsers)
- ❌ No cross-tab support
- ❌ Limited network interception

**Best For | সেরা ব্যবহার:**

- Learning automation testing
- Single browser testing
- Interactive debugging
- Developer-focused teams

**Installation | ইনস্টলেশন:**

```bash
npm install cypress --save-dev
npx cypress open
```

---

### Selenium 🌐

**Pros | সুবিধা:**

- ✅ Industry standard
- ✅ Supports all major browsers
- ✅ Mature ecosystem
- ✅ Large community
- ✅ Multi-language support
- ✅ Works with legacy apps

**Cons | অসুবিধা:**

- ❌ Slowest execution
- ❌ More flaky (timing issues)
- ❌ Verbose code required
- ❌ Steeper learning curve
- ❌ Limited shadow DOM support

**Best For | সেরা ব্যবহার:**

- Legacy applications
- Enterprise environments
- Multi-browser compatibility
- Java/Python projects

**Installation | ইনস্টলেশন:**

```bash
npm install selenium-webdriver
npm install chromedriver
```

---

## 📊 Side-by-Side Comparison | পাশাপাশি তুলনা

| Feature | সুবিধা | Playwright | Cypress | Selenium |
| --- | --- | --- | --- | --- |
| **Speed** | গতি | ⚡⚡⚡ | ⚡⚡ | ⚡ |
| **Browsers** | ব্রাউজার | Chromium, Firefox, WebKit | Chrome, Edge, Firefox | All Major |
| **Parallel Execution** | সমান্তরাল চালনা | ✅ | ✅ | ✅ |
| **Network Interception** | নেটওয়ার্ক বাধা | ✅ | ⚠️ Limited | ⚠️ Limited |
| **Shadow DOM** | Shadow DOM | ✅ | ✅ | ❌ |
| **Debugging** | ডিবাগিং | ✅ | ✅✅ | ✅ |
| **API Quality** | API গুণমান | ✅✅✅ | ✅✅ | ⚠️ Complex |
| **Documentation** | ডকুমেন্টেশন | ✅✅✅ | ✅✅✅ | ✅✅ |
| **Learning Curve** | শেখার বক্ররেখা | Moderate | Easy | Hard |
| **Mobile Web** | মোবাইল ওয়েব | ✅ | ✅ | ✅ |
| **File Upload** | ফাইল আপলোড | ✅ | ✅ | ✅ |
| **File Download** | ফাইল ডাউনলোড | ✅ | ⚠️ | ❌ |
| **Geolocation** | জিওলোকেশন | ✅ | ❌ | ✅ |
| **Permissions** | অনুমতি | ✅ | ❌ | ✅ |
| **Community Size** | কমিউনিটি আকার | Growing | Large | Very Large |

---

## 🔧 Common Syntax Comparison | সাধারণ সিনট্যাক্স তুলনা

### Navigation | নেভিগেশন

**Playwright:**

```jsx
await page.goto('https://example.com');
await page.waitForLoadState('networkidle');
```

**Cypress:**

```jsx
cy.visit('https://example.com');
cy.wait(3000); // or use cy.waitForElement
```

**Selenium:**

```jsx
await driver.get('https://example.com');
await driver.wait(until.titleIs('Title'), 5000);
```

---

### Finding Elements | উপাদান খুঁজে পাওয়া

**Playwright:**

```jsx
const element = page.locator('button:has-text("Click me")');
await element.click();
```

**Cypress:**

```jsx
cy.contains('button', 'Click me').click();
```

**Selenium:**

```jsx
const element = await driver.findElement(By.xpath('//button[contains(text(), "Click me")]'));
await element.click();
```

---

### Waiting | অপেক্ষা করা

**Playwright:**

```jsx
await page.waitForSelector('.element', { timeout: 5000 });
await page.waitForLoadState('networkidle');
await page.waitForFunction(() => document.title === 'New Title');
```

**Cypress:**

```jsx
cy.get('.element').should('be.visible'); // implicit wait
cy.wait('@api'); // wait for network request
cy.waitForElement('.element', { timeout: 5000 }); // explicit
```

**Selenium:**

```jsx
await driver.wait(until.elementLocated(By.css('.element')), 5000);
await driver.wait(until.elementIsVisible(element), 5000);
thread.sleep(5000); // hard wait (NOT RECOMMENDED)
```

---

### Assertions | নিশ্চিতকরণ

**Playwright:**

```jsx
await expect(element).toBeVisible();
await expect(element).toHaveText('Expected');
await expect(element).toHaveAttribute('href', '/path');
```

**Cypress:**

```jsx
cy.get(element).should('be.visible');
cy.get(element).should('have.text', 'Expected');
cy.get(element).should('have.attr', 'href', '/path');
```

**Selenium:**

```jsx
const text = await element.getText();
assert.equal(text, 'Expected');
```

---

### Handling Multiple Elements | একাধিক উপাদান পরিচালনা

**Playwright:**

```jsx
const elements = await page.$$('.item');
for (const element of elements) {
  await element.click();
}
```

**Cypress:**

```jsx
cy.get('.item').each(($element) => {
  cy.wrap($element).click();
});
```

**Selenium:**

```jsx
const elements = await driver.findElements(By.css('.item'));
for (const element of elements) {
  await element.click();
}
```

---

### Handling iFrames | iFrame পরিচালনা

**Playwright:**

```jsx
const frameLocator = page.frameLocator('iframe');
const element = frameLocator.locator('button');
await element.click();
```

**Cypress:**

```jsx
cy.get('iframe').then(($iframe) => {
  const body = $iframe.contents().find('body');
  cy.wrap(body).find('button').click();
});
```

**Selenium:**

```jsx
await driver.switchTo().frame(0);
const button = await driver.findElement(By.css('button'));
await button.click();
await driver.switchTo().defaultContent();
```

---

### Drag and Drop | ড্র্যাগ এবং ড্রপ

**Playwright:**

```jsx
await source.dragTo(target);
// or
await page.mouse.move(source.x, source.y);
await page.mouse.down();
await page.mouse.move(target.x, target.y);
await page.mouse.up();
```

**Cypress:**

```jsx
cy.get('.draggable').trigger('mousedown')
  .trigger('mousemove', { clientX: x, clientY: y })
  .trigger('mouseup');
// or use a drag-drop library
```

**Selenium:**

```jsx
const actions = driver.actions({ async: true });
await actions.dragAndDrop(source, target).perform();
```

---

### File Upload | ফাইল আপলোড

**Playwright:**

```jsx
await page.locator('input[type="file"]').setInputFiles('./path/to/file.pdf');
```

**Cypress:**

```jsx
cy.get('input[type="file"]').selectFile('./path/to/file.pdf');
```

**Selenium:**

```jsx
const fileInput = await driver.findElement(By.css('input[type="file"]'));
await fileInput.sendKeys('/absolute/path/to/file.pdf');
```

---

### Handling Pop-ups | পপ-আপ পরিচালনা

**Playwright:**

```jsx
const newPage = await context.waitForEvent('page');
await page.locator('a').click();
const title = await newPage.title();
await newPage.close();
```

**Cypress:**

```jsx
cy.window().then((win) => {
  cy.stub(win, 'open').returns(window);
});
cy.get('a').click();
```

**Selenium:**

```jsx
const originalWindow = await driver.getWindowHandle();
await driver.findElement(By.css('a')).click();
await driver.wait(until.numberOfWindowsIsGreaterThan(1), 5000);
const windows = await driver.getAllWindowHandles();
await driver.switchTo().window(windows[1]);
await driver.close();
await driver.switchTo().window(originalWindow);
```

---

## 💡 Recommendations | সুপারিশগুলি

### For Beginners | শিক্ষানবিসদের জন্য

**Recommended: Cypress** 🌳

- Easy to learn
- Excellent debugging
- Great documentation
- Active community

### For Production Systems | উৎপাদন সিস্টেমের জন্য

**Recommended: Playwright** ⚡

- Fast and reliable
- Modern API
- Good for CI/CD
- Excellent support

### For Enterprise | এন্টারপ্রাইজের জন্য

**Recommended: Selenium** 🌐

- Industry standard
- Supports all browsers
- Large community
- Multi-language support

### For Modern Web Apps | আধুনিক ওয়েব অ্যাপের জন্য

**Recommended: Playwright** ⚡

- Best for SPAs
- Shadow DOM support
- Network mocking
- Mobile testing

---

## 📚 Learning Resources | শেখার সংস্থান

### Playwright

- Official: [https://playwright.dev](https://playwright.dev)
- GitHub: [https://github.com/microsoft/playwright](https://github.com/microsoft/playwright)
- Community: Discord, GitHub Discussions

### Cypress

- Official: [https://cypress.io](https://cypress.io)
- GitHub: [https://github.com/cypress-io/cypress](https://github.com/cypress-io/cypress)
- Community: Slack, GitHub Discussions

### Selenium

- Official: [https://selenium.dev](https://selenium.dev)
- Documentation: [https://www.selenium.dev/documentation/](https://www.selenium.dev/documentation/)
- Community: SeleniumHQ, StackOverflow

---

*Framework comparison updated: April 2026*

*ফ্রেমওয়ার্ক তুলনা আপডেট: এপ্রিল 2026*
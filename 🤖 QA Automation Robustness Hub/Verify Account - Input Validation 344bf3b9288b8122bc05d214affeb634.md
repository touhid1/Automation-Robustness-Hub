# Verify Account - Input Validation

Category: Form Elements, Interactions
Difficulty: Easy
Framework: Cypress, Playwright
Priority: 2
Status: Not Started

## Challenge: Verify Account - Input Validation

### বিবরণ | Description

সঠিক কোড ইনপুট করে অ্যাকাউন্ট যাচাই করুন। Key-up button বা সরাসরি টাইপিং দ্বারা সংখ্যা প্রবেশ করুন।

Enter valid code by pressing the key-up button or typing number and assert success message.

### সেরা অনুশীলন | Best Practices

- ✅ Single-character inputs এর জন্য individual fields ব্যবহার করুন
- ✅ Focus management track করুন
- ✅ Keyboard events এবং direct input উভয় test করুন
- ✅ Success message visibility অপেক্ষা করুন

### সাধারণ সমস্যা | Common Pitfalls

❌ Auto-focus behavior ignore করা

❌ Validation messages load না হওয়া পর্যন্ত wait না করা

❌ Different input methods test না করা

### সমাধান কোড | Solution Code

```jsx
// Playwright
await page.goto('https://qaplayground.dev/apps/verify-account/');
const codeFields = await page.$$('input[type="text"]');
const code = ['1', '2', '3', '4'];

for (let i = 0; i < codeFields.length; i++) {
  await codeFields[i].fill(code[i]);
}

await page.waitForSelector('.success-message');
const message = await page.locator('.success-message').textContent();
expect(message).toContain('Success');
```
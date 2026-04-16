# File Upload & Download

Category: File Operations
Difficulty: Medium
Framework: Cypress, Playwright, Selenium
Priority: 10
Status: Not Started

## Challenge: File Upload & Download

### আপলোড | Upload

ইমেজ ফাইল আপলোড করুন এবং ফাইল নাম assert করুন।

Upload an image file and assert the file's name.

### ডাউনলোড | Download

ফাইল ডাউনলোড করুন এবং ফাইলের নাম এবং সাইজ assert করুন।

Download a file and assert the file's name and size.

### সেরা অনুশীলন | Best Practices

- ✅ setInputFiles() ব্যবহার করুন file input এর জন্য
- ✅ waitForEvent('download') ব্যবহার করুন downloads এর জন্য
- ✅ File paths properly handle করুন
- ✅ Downloaded file properties verify করুন
- ✅ Cleanup temporary files

### সাধারণ সমস্যা | Common Pitfalls

❌ File browser dialog না খোলা সত্ত্বেও interact করা

❌ Download complete না হওয়া পর্যন্ত access করা

❌ File path validation না করা

### সমাধান কোড | Solution Code

```jsx
// Playwright Upload
await page.goto('https://qaplayground.dev/apps/upload/');
await page.locator('input[type="file"]').setInputFiles('./test-image.png');
const fileName = await page.locator('.file-name').textContent();
expect(fileName).toBe('test-image.png');

// Download
const downloadPromise = context.waitForEvent('download');
await page.locator('a:has-text("Download")').click();
const download = await downloadPromise;
expect(download.suggestedFilename()).toBe('document.pdf');
```
# 📖 QA Automation Robustness Guide - সম্পূর্ণ নির্দেশিকা

# QA Automation Robustness Hub Guide

# QA স্বয়ংক্রিয়তা দৃঢ়তা কেন্দ্র গাইড

## 🎯 Overview | সংক্ষিপ্ত বিবরণ

This hub is designed to help QA engineers master automation testing by solving real-world challenges from [**QAPlayground.dev**](http://QAPlayground.dev) using modern frameworks like Playwright, Cypress, and Selenium.

এই কেন্দ্রটি QA ইঞ্জিনিয়ারদের [QAPlayground.dev](http://QAPlayground.dev) এর বাস্তব চ্যালেঞ্জগুলি সমাধান করে স্বয়ংক্রিয় পরীক্ষায় দক্ষতা অর্জন করতে সহায়তা করার জন্য ডিজাইন করা হয়েছে।

---

## 🚀 Getting Started | শুরু করা

### Step 1: Choose Your Framework | আপনার ফ্রেমওয়ার্ক বেছে নিন

**Playwright** (Recommended ✨)

- Fast, reliable, cross-browser support
- Modern API with great documentation
- Best for modern testing needs

**Cypress**

- Excellent debugging experience
- Great for beginners
- Strong community support

**Selenium**

- Industry standard
- Mature ecosystem
- Good for legacy projects

### Step 2: Pick a Challenge | একটি চ্যালেঞ্জ বেছে নিন

1. Start with **Easy** difficulty challenges
2. Progress to **Medium** and **Hard**
3. Check multiple categories to build comprehensive skills

### Step 3: Study the Solution | সমাধান অধ্যয়ন করুন

- Read the provided code example
- Understand the approach
- Identify best practices
- Note common pitfalls

### Step 4: Implement & Test | বাস্তবায়ন এবং পরীক্ষা করুন

- Write your own solution first
- Test on [qaplayground.dev](http://qaplayground.dev)
- Compare with provided solution
- Iterate and improve

---

## 🏆 Best Practices | সেরা অনুশীলনগুলি

### 1. Use Explicit Waits | স্পষ্ট অপেক্ষা ব্যবহার করুন

❌ **Bad:**

```jsx
await page.wait(5000); // Hard-coded delay
```

✅ **Good:**

```jsx
await page.waitForSelector('.element', { timeout: 5000 });
await page.waitForLoadState('networkidle');
```

### 2. Avoid Hard-Coded Selectors | কঠোর নির্ধারিত নির্বাচক এড়িয়ে চলুন

❌ **Bad:**

```jsx
await page.click('body > div:nth-child(2) > table > tbody > tr:nth-child(1) > td:nth-child(2) > button');
```

✅ **Good:**

```jsx
await page.locator('button:has-text("Submit")').click();
```

### 3. Handle Dynamic Content | গতিশীল সামগ্রী পরিচালনা করুন

✅ **Best Practice:**

- Use contains() for text matching
- Leverage CSS combinators
- Use nth-child() only as last resort
- Test with dynamic data

### 4. Master DOM Handling | DOM পরিচালনা করুন

- **iframe handling:** frameLocator() with proper sequencing
- **Shadow DOM:** Use pierce (>>>) combinator
- **Dynamic lists:** getAll() then loop/filter
- **Nested elements:** Chain locators carefully

### 5. Browser Feature Testing | ব্রাউজার বৈশিষ্ট্য পরীক্ষা করুন

✅ **Key Areas:**

- File uploads/downloads
- Geolocation & permissions
- Local storage & sessions
- Service workers
- Network throttling

### 6. Error Handling & Debugging | ত্রুটি পরিচালনা এবং ডিবাগিং

```jsx
try {
  await page.goto(url, { waitUntil: 'networkidle', timeout: 30000 });
} catch (error) {
  console.error('Navigation failed:', error);
  await page.screenshot({ path: 'error.png' });
  throw error;
}
```

---

## 📊 Challenge Categories Breakdown | চ্যালেঞ্জ বিভাগগুলি বিশ্লেষণ

### 🎯 Form Elements (ফর্ম উপাদান)

- Verify Account
- Tags Input Box
- Rating Widget
- Budget Tracker

**Key Skills:** Input handling, validation, form submission

### 🧭 Navigation (নেভিগেশন)

- Multi-Level Dropdown
- New Tab Handling
- Links Navigation
- Redirect Chains

**Key Skills:** Menu handling, link verification, window switching

### 🔄 Interactions (মিথস্ক্রিয়া)

- Drag and Drop
- Mouse Hover
- Context Menu (Right-Click)
- Sortable Lists

**Key Skills:** Advanced mouse events, action sequences

### 🎪 DOM Handling (DOM পরিচালনা)

- Dynamic Table
- Nested iFrame
- Shadow DOM
- Covered Elements

**Key Skills:** Selector strategies, DOM traversal, element visibility

### 📁 File Operations (ফাইল অপারেশন)

- Upload File
- Download File

**Key Skills:** File I/O, permission handling, network interception

### ⚡ Dynamic Content (গতিশীল সামগ্রী)

- Fetching Data
- QR Code Generation
- Budget Tracker (CRUD)

**Key Skills:** API testing, async operations, state management

### 🌐 Browser Features (ব্রাউজার বৈশিষ্ট্য)

- Pop-Up Window
- Geolocation
- Onboarding Modal
- Changeable iFrame

**Key Skills:** Browser context, permissions, event handling

### 🔌 API Testing (API পরীক্ষা)

- Fetch & Wait
- Network Interception
- Request/Response Validation

**Key Skills:** Network monitoring, async assertions

---

## ⚠️ Common Pitfalls to Avoid | এড়ানোর জন্য সাধারণ ফাঁদগুলি

| Pitfall | সমস্যা | Solution | সমাধান |
| --- | --- | --- | --- |
| Hard-coded delays | নির্দিষ্ট বিলম্ব | Use explicit waits | স্পষ্ট অপেক্ষা ব্যবহার করুন |
| Stale element | পুরানো উপাদান | Re-query elements | উপাদানগুলি পুনরায় অনুসন্ধান করুন |
| Not waiting for navigation | নেভিগেশন অপেক্ষা না করা | Wait for load state | লোড অবস্থার জন্য অপেক্ষা করুন |
| Forgetting iframe context | iframe প্রেক্ষাপট ভুলে যাওয়া | Use frameLocator() | frameLocator() ব্যবহার করুন |
| Ignoring Shadow DOM | Shadow DOM উপেক্ষা করা | Use pierce combinator | pierce combinator ব্যবহার করুন |
| Race conditions | প্রতিযোগিতামূলক অবস্থা | Proper synchronization | সঠিক সিঙ্ক্রোনাইজেশন |
| Missing error handling | ত্রুটি পরিচালনা অনুপলব্ধ | Try-catch blocks | Try-catch ব্লক ব্যবহার করুন |

---

## 🎓 Learning Path | শেখার পথ

### Week 1-2: Foundations (ভিত্তি)

1. ✅ Verify Account (Easy)
2. ✅ Mouse Hover (Easy)
3. ✅ Links Navigation (Easy)

### Week 3-4: DOM Mastery (DOM দক্ষতা)

1. 🔷 Dynamic Table (Medium)
2. 🔷 Tags Input Box (Medium)
3. 🔷 Multi-Level Dropdown (Medium)

### Week 5-6: Advanced Interactions (উন্নত মিথস্ক্রিয়া)

1. 🔴 Sortable List - Drag & Drop (Hard)
2. 🔴 Nested iFrame (Hard)
3. 🔴 Shadow DOM (Hard)

### Week 7-8: Browser & API (ব্রাউজার ও API)

1. 🔷 File Operations (Medium)
2. 🔷 Geolocation (Medium)
3. 🔷 Fetching Data (Medium)

---

## 🛠️ Setup Instructions | সেটআপ নির্দেশাবলী

### For Playwright | প্লেরাইট এর জন্য

```bash
npm init playwright@latest
cd playwright-tests
npm install
```

### For Cypress | সাইপ্রেসের জন্য

```bash
npm install cypress --save-dev
npx cypress open
```

### For Selenium | সেলেনিয়াম এর জন্য

```bash
npm install selenium-webdriver
npm install webdriver-manager
```

---

## 📚 Resources | সম্পদ

### Official Documentation | অফিসিয়াল ডকুমেন্টেশন

- [Playwright Docs](https://playwright.dev)
- [Cypress Docs](https://docs.cypress.io)
- [Selenium Docs](https://selenium.dev)

### QA Playground | QA খেলার মাঠ

- [QAPlayground.dev](http://QAPlayground.dev)
- [GitHub Solutions](https://github.com/marko-simic/qa-playground-tests)

### Best Practices Guides | সেরা অনুশীলন গাইড

- Testing Library Best Practices
- Playwright Inspector
- Cypress Real World Testing

---

## 💡 Tips for Success | সাফল্যের টিপস

1. **Start Small** - Begin with easy challenges
2. **Read Solutions** - Study provided code carefully
3. **Practice** - Write your own implementation
4. **Debug** - Use browser DevTools and inspect mode
5. **Document** - Keep notes on learnings
6. **Share** - Discuss solutions with peers
7. **Iterate** - Refactor and optimize your code
8. **Test Thoroughly** - Test edge cases and error scenarios

---

## 🔗 Challenge Database Navigation | চ্যালেঞ্জ ডাটাবেস নেভিগেশন

### View Options:

- **📊 By Difficulty Level** - See challenges grouped by difficulty
- **✅ Progress Tracker** - Track your progress through each challenge
- **All Challenges** - Browse complete list with all details

### Property Filters:

- **Status:** Not Started → In Progress → Completed
- **Difficulty:** Easy → Medium → Hard
- **Framework:** Playwright, Cypress, Selenium, WebdriverIO
- **Category:** Form Elements, Navigation, Interactions, etc.

---

## 🎉 Closing Notes | সমাপনী নোট

Automation testing is both an art and a science. The challenges in [QAPlayground.dev](http://QAPlayground.dev) provide excellent real-world scenarios that reflect actual testing needs. 

স্বয়ংক্রিয়তা পরীক্ষা একটি শিল্প এবং বিজ্ঞান উভয়ই। [QAPlayground.dev](http://QAPlayground.dev) এর চ্যালেঞ্জগুলি দুর্দান্ত বাস্তব-বিশ্বের পরিস্থিতি প্রদান করে যা প্রকৃত পরীক্ষার চাহিদা প্রতিফলিত করে।

By mastering these challenges, you'll develop:

- ✨ Strong foundation in automation principles
- 🎯 Problem-solving skills
- 🔧 Framework expertise
- 📈 Confidence in complex scenarios

Happy Testing! 🚀

---

*Last Updated: April 2026*

*সর্বশেষ আপডেট: এপ্রিল 2026*
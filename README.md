## 測試 Button


### 安裝
```
npm install --save jest-puppeteer puppeteer jest
```
### 修改 package.json

```json
    "jest": {
        "testMatch": [
             "<rootDir>/src/**/__tests__/**/*.{js,jsx,ts,tsx}",
           - "<rootDir>/src/**/?(*.)(spec|test).{js,jsx,ts,tsx}"
           + "<rootDir>/src/**/?(*.)(spec|test|e2e).{js,jsx,ts,tsx}"
        ],
    }
```
### App.e2e.js

```js
import puppeteer from "puppeteer";

describe("Google", () => {
  let browser;
  let page;
  beforeAll(async () => {
    browser = await puppeteer.launch({ headless: false });
    page = await browser.newPage();
  });
  afterEach(async () => {
    // await browser.close();
  });

  it("should load the page", async () => {
    await page.goto("https://www.google.com", { timeout: 50000 });
    await page.evaluate(() => {
      debbuger;
    });
  });
});

```


### 執行測試

```
npm run test
```

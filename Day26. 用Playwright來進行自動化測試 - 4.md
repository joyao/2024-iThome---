## Authentication
測試需要登入的情形，並保留登入狀態

先註冊 [https://parabank.parasoft.com/parabank/index.htm]([https://parabank.parasoft.com/parabank/index.htm](https://parabank.parasoft.com/parabank/index.htm))

![[Pasted image 20240909004059.png]]

輸入資料

![[Pasted image 20240909004402.png]]

``` bash
npx playwright codegen --save-storage=auth.json parabank.parasoft.com
```


開啟網頁並進行登入
則auth.json會類似這樣

```json
{
  "cookies": [
    {
      "name": "JSESSIONID",
      "value": "EED17FDC6CFC3893C16877E3BF45C6B7",
      "domain": "parabank.parasoft.com",
      "path": "/parabank",
      "expires": -1,
      "httpOnly": true,
      "secure": false,
      "sameSite": "Lax"
    }
  ],
  "origins": []
}
```

為了不要每次都登入

```bash
npx playwright codegen --load-storage=auth.json parabank.parasoft.com
```

一打開就是已登入狀態

![[Pasted image 20240909005646.png]]

可以看到 inspector的code會長這樣

```js
test.use({
	storageState: 'auth.json'
})
```

![[Pasted image 20240909005748.png]]

所以我們的目的是第一次測試的時候執行登入，則後面的都用第一次登入的資訊

### 儲存登入資訊

```js
const { test, expect } = require('@playwright/test');

test.describe("Authentication", () => {

    test("Saving Authentication", async ({page}) => {
        await page.goto('https://parabank.parasoft.com/parabank/index.htm;jsessionid=D1A733DE3162A28C535B247C7CB6F29D');
        await page.locator('input[name="username"]').click();
        await page.locator('input[name="username"]').fill('demo');
        await page.locator('input[name="password"]').click();
        await page.locator('input[name="password"]').fill('demo');
        await page.getByRole('button', { name: 'Log In' }).click();

        await page.context().storageState({path: 'automationUser.json'});
    })
})
```

### 利用登入資訊進行測試

``` js
const { test, expect } = require('@playwright/test');

test.describe("Authentication", () => {
    test.use({
        storageState: "automationUser.json"
    })

    test.beforeEach(async ({page}) => {
        await page.goto("https://parabank.parasoft.com")
    })

    test.skip("Saving Authentication", async ({page}) => {
        await page.goto('https://parabank.parasoft.com/parabank/index.htm;jsessionid=D1A733DE3162A28C535B247C7CB6F29D');
        await page.locator('input[name="username"]').click();
        await page.locator('input[name="username"]').fill('demo');
        await page.locator('input[name="password"]').click();
        await page.locator('input[name="password"]').fill('demo');
        await page.getByRole('button', { name: 'Log In' }).click();

        await page.context().storageState({path: 'automationUser.json'});
    })

    test("Test 2", async ({page}) => {
        await page.getByRole('link', { name: 'Transfer Funds' }).first().click();
    })

    test("Test 3", async ({page}) => {
        await page.getByRole('link', { name: 'Bill Pay' }).first().click();
    })


})
```

## Emulation 模擬器

模擬設備來進行測試

``` bash
npx playwright codegen --device='iPhone 11' wikipedia.org
```

![[Pasted image 20240909221827.png]]

就可以模擬iphone 11用safari來開啟wikipedia.org網頁

假設你輸入了一個錯誤或沒支援的device

``` bash
npx playwright codegen --device='iPhone 111' wikipedia.org
```

則會收到以下錯誤訊息，並列出所有支援的設備列表，我們可以依照這個類表去模擬設備進行測試

```
Error: Device descriptor not found: 'iPhone 111', available devices are:
  "Blackberry PlayBook"
  "Blackberry PlayBook landscape"
  "BlackBerry Z30"
  "BlackBerry Z30 landscape"
  "Galaxy Note 3"
  "Galaxy Note 3 landscape"
  "Galaxy Note II"
  "Galaxy Note II landscape"
  "Galaxy S III"
  "Galaxy S III landscape"
  "Galaxy S5"
  "Galaxy S5 landscape"
  "Galaxy S8"
  "Galaxy S8 landscape"
  "Galaxy S9+"
  "Galaxy S9+ landscape"
  "Galaxy Tab S4"
  "Galaxy Tab S4 landscape"
  "iPad (gen 5)"
  "iPad (gen 5) landscape"
  "iPad (gen 6)"
  "iPad (gen 6) landscape"
  "iPad (gen 7)"
  "iPad (gen 7) landscape"
  "iPad Mini"
  "iPad Mini landscape"
  "iPad Pro 11"
  "iPad Pro 11 landscape"
  "iPhone 6"
  "iPhone 6 landscape"
  "iPhone 6 Plus"
  "iPhone 6 Plus landscape"
  "iPhone 7"
  "iPhone 7 landscape"
  "iPhone 7 Plus"
  "iPhone 7 Plus landscape"
  "iPhone 8"
  "iPhone 8 landscape"
  "iPhone 8 Plus"
  "iPhone 8 Plus landscape"
  "iPhone SE"
  "iPhone SE landscape"
  "iPhone X"
  "iPhone X landscape"
  "iPhone XR"
  "iPhone XR landscape"
  "iPhone 11"
  "iPhone 11 landscape"
  "iPhone 11 Pro"
  "iPhone 11 Pro landscape"
  "iPhone 11 Pro Max"
  "iPhone 11 Pro Max landscape"
  "iPhone 12"
  "iPhone 12 landscape"
  "iPhone 12 Pro"
  "iPhone 12 Pro landscape"
  "iPhone 12 Pro Max"
  "iPhone 12 Pro Max landscape"
  "iPhone 12 Mini"
  "iPhone 12 Mini landscape"
  "iPhone 13"
  "iPhone 13 landscape"
  "iPhone 13 Pro"
  "iPhone 13 Pro landscape"
  "iPhone 13 Pro Max"
  "iPhone 13 Pro Max landscape"
  "iPhone 13 Mini"
  "iPhone 13 Mini landscape"
  "iPhone 14"
  "iPhone 14 landscape"
  "iPhone 14 Plus"
  "iPhone 14 Plus landscape"
  "iPhone 14 Pro"
  "iPhone 14 Pro landscape"
  "iPhone 14 Pro Max"
  "iPhone 14 Pro Max landscape"
  "iPhone 15"
  "iPhone 15 landscape"
  "iPhone 15 Plus"
  "iPhone 15 Plus landscape"
  "iPhone 15 Pro"
  "iPhone 15 Pro landscape"
  "iPhone 15 Pro Max"
  "iPhone 15 Pro Max landscape"
  "Kindle Fire HDX"
  "Kindle Fire HDX landscape"
  "LG Optimus L70"
  "LG Optimus L70 landscape"
  "Microsoft Lumia 550"
  "Microsoft Lumia 550 landscape"
  "Microsoft Lumia 950"
  "Microsoft Lumia 950 landscape"
  "Nexus 10"
  "Nexus 10 landscape"
  "Nexus 4"
  "Nexus 4 landscape"
  "Nexus 5"
  "Nexus 5 landscape"
  "Nexus 5X"
  "Nexus 5X landscape"
  "Nexus 6"
  "Nexus 6 landscape"
  "Nexus 6P"
  "Nexus 6P landscape"
  "Nexus 7"
  "Nexus 7 landscape"
  "Nokia Lumia 520"
  "Nokia Lumia 520 landscape"
  "Nokia N9"
  "Nokia N9 landscape"
  "Pixel 2"
  "Pixel 2 landscape"
  "Pixel 2 XL"
  "Pixel 2 XL landscape"
  "Pixel 3"
  "Pixel 3 landscape"
  "Pixel 4"
  "Pixel 4 landscape"
  "Pixel 4a (5G)"
  "Pixel 4a (5G) landscape"
  "Pixel 5"
  "Pixel 5 landscape"
  "Pixel 7"
  "Pixel 7 landscape"
  "Moto G4"
  "Moto G4 landscape"
  "Desktop Chrome HiDPI"
  "Desktop Edge HiDPI"
  "Desktop Firefox HiDPI"
  "Desktop Safari"
  "Desktop Chrome"
  "Desktop Edge"
  "Desktop Firefox"
```


## 其他的emulation選項
emulatioin不只有可以模擬device
還可以模擬主題顏色、位置、viewport size
``` bash
# viewport size
npx playwright codegen --viewport-size=800,600 playwright.dev
# color scheme
npx playwright codegen --color-scheme=dark playwright.dev
# geolocation, language and timezone
npx playwright codegen --timezone="Europe/Rome" --geolocation="41.890221,12.492348" --lang="it-IT" bing.com/maps
```


## Trace Viewer

可以去trace畫面和每個步驟的執行時間

在設定檔中可以設定
``` json
const config = {
	use: {
        trace: 'on',
	},
}
```

可用選項
- `'on-first-retry'` - Record a trace only when retrying a test for the first time.
- `'on-all-retries'` - Record traces for all test retries.
- `'off'` - Do not record a trace.
- `'on'` - Record a trace for each test. (not recommended as it's performance heavy)
- `'retain-on-failure'` - Record a trace for each test, but remove it from successful test runs.


執行測試後則會在資料夾中有一個test-results
![[Pasted image 20240909222734.png]]


``` bash
npx playwright show-trace <trace.zip path>
```

For example
``` bash
npx playwright show-trace D:\Share\Playground\Playwright\test-results\example3-Authentication-Test-3-chromium\trace.zip
```

![[Pasted image 20240909222956.png]]

## Local configuration

也就是不是全域的設定，而是不同的test case有自己的設定

例如設定單一一個test case的viewport
``` js
test.use({ viewport: { width: 600, height: 900 } });
```


## 其他的cli相關的設定選項

``` bash
# Debug mode
npx playwright test example3.spec.js --debug --parject=chrome
# Timeout (miliseconds)
npx playwright test example3.spec.js --timeout=5000
# List tests
npx playwright test --list
# Setup global timeout
npx playwright test --global-timeout=6000
# 可以忍受的最大錯誤量，超過則停止測試
npx playwright test --max-failures=6
# Retry when fails
npx playwright test --retries=3
```

## 平行測試

``` bash
npx playwright test --workers 4
```

在同一個檔案內的平行測試

```js
import { test } from '@playwright/test';  
  
test.describe.configure({ mode: 'parallel' });  
  
test('runs in parallel 1', async ({ page }) => { /* ... */ });  
test('runs in parallel 2', async ({ page }) => { /* ... */ });
```


## Drag and drop

https://playwright.dev/docs/input#drag-and-drop

```js

const { test, expect } = require('@playwright/test');

test.describe("Example tests", () => {

    test("Examples", async ({ page }) => {
	    await page.goto("https://the-internet.herokuapp.com/drag_and_drop");
	    await page.dragAndDrip("#column-a", "#column-b");
	    await page.dragAndDrip("#column-b", "#column-a");
	    await page.pause();
    })

})

```

## Dropdown

https://the-internet.herokuapp.com/dropdown

```js
const { test, expect } = require('@playwright/test');

test.describe("Example tests", () => {

    test("Examples", async ({ page }) => {
	    await page.goto("https://the-internet.herokuapp.com/dropdown");
	    await page.locator("#dropdown").selectOption({label: 'Option 1'});
	    await expect(page.locator('#dropdown')).tohaveValue('1')
	    await page.locator("#dropdown").selectOption({label: 'Option 2'});
	    await expect(page.locator('#dropdown')).tohaveValue('2')
    })
})
```

## iFrame

https://the-internet.herokuapp.com/iframe

![[Pasted image 20240909235346.png]]

```js
const { test, expect } = require('@playwright/test');

test.describe("Example tests", () => {

    test("Examples", async ({ page }) => {
	    await page.goto("https://the-internet.herokuapp.com/iframe");
	    const frameTest = page.frameLocator("#mce_0_ifr").locator('html');
	    await frameTest.click();
	    await frameTest.type("This is just a test typing in iframe");
    })
})
```



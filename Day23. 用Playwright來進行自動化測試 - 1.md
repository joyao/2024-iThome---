
https://playwright.dev/

- Playwright是用來進行E2E的自動化
- 由Microsoft開發與維護

## 什麼是Playwright

### 特色
- 跨瀏覽器
- 跨平台
- 跨不同程式語言
- 可以測試手機網頁

### 有彈性的架構:
- Auto-waiting
- Web-first assertions
- Tracing

### No trade-offs and limits
- 支援多tabs, users
- Trusted Events
- Test Frames and shadow dom

### Full isolation and fast execution
- Browser Context
- Log in once

### 強大的工具
- Codegen
- Playwright Inspector
- Trace Viewer

## 步驟

安裝nodejs, vscode

新增Playwright專案
``` bash
cd /d D:\Share\Playground\Playwright
npm init playwright@latest
```

全部都依照預設值
用vs code開啟

![[Pasted image 20240906234343.png]]

有提供一個範例測試檔案：example.spec.js

``` js
// @ts-check
const { test, expect } = require('@playwright/test');

test('has title', async ({ page }) => {
  await page.goto('https://playwright.dev/');

  // Expect a title "to contain" a substring.
  await expect(page).toHaveTitle(/Playwright/);
});

test('get started link', async ({ page }) => {
  await page.goto('https://playwright.dev/');

  // Click the get started link.
  await page.getByRole('link', { name: 'Get started' }).click();

  // Expects page to have a heading with the name of Installation.
  await expect(page.getByRole('heading', { name: 'Installation' })).toBeVisible();
});

```

直接執行看看
``` bash
npx playwright test
```

![[Pasted image 20240906234716.png]]

```
npx playwright show-report
```

![[Pasted image 20240906234756.png]]
(這介面有點像github)

也可以加pause 和cmd加--headed，可以用來inspect網頁
一般情形都是headless，所以不會看到背景執行的網頁

``` js
test('pause check', async ({ page }) => {
  await page.goto('https://playwright.dev/');
  await page.pause()
});

```

``` bash
npx playwright test --headed
```

![[Pasted image 20240906235408.png]]

### 指定瀏覽器

``` bash
npx playwright test example.spec.js --headed --browser=firefox
```

### 打錯檔案名
會顯示no tests found
```
PS D:\Share\Playground\Playwright> npx playwright test tests/test.spec.js
Error: No tests found.
Make sure that arguments are regular expressions matching test files.
You may need to escape symbols like "$" or "*" and quote the arguments.
```

### 利用selector來抓到你要的Element

``` js
// Want to find the element with text "Add/Remove Elements"
// Method 1
await page.locator("text=Add/Remove Elements").click();

// Method 2
await page.click("text=Add/Remove Elements");

// Method 3
const element = .locator("text=Add/Remove Elements")
await element.click()
```


### Annotations

- [test.skip()](https://playwright.dev/docs/api/class-test#test-skip) marks the test as irrelevant. Playwright does not run such a test. Use this annotation when the test is not applicable in some configuration.
- [test.fail()](https://playwright.dev/docs/api/class-test#test-fail) marks the test as failing. Playwright will run this test and ensure it does indeed fail. If the test does not fail, Playwright will complain.
- [test.fixme()](https://playwright.dev/docs/api/class-test#test-fixme) marks the test as failing. Playwright will not run this test, as opposed to the `fail` annotation. Use `fixme` when running the test is slow or crashes.
- [test.slow()](https://playwright.dev/docs/api/class-test#test-slow) marks the test as slow and triples the test timeout.

#### Focus a test

如果有很多測項，但我只想要跑一個，可以使用test.only

``` js
const { test, expect } = require('@playwright/test');

test.only('pause check', async ({ page }) => {
  // Run only focused tests in the entire project.
  await page.goto('https://playwright.dev/');
  await page.pause()
});

```

#### Skip a test

```js
const { test, expect } = require('@playwright/test');

test.skip('pause check', async ({ page }) => {
  // This test is not run
  await page.goto('https://playwright.dev/');
  await page.pause()
});

```

#### Conditionally skip a test

假設某個測項不能在firefox上執行
```js
const { test, expect } = require('@playwright/test');

test('Skip pause check', async ({ page }) => {
  // If browser is firefox, run
  test.skip(browserName === 'firefox', 'Still working on it');
  await page.goto('https://playwright.dev/');
  await page.pause()
});

```


#### Tag tests
利用tag來執行相對應檔案
```js
import { test, expect } from '@playwright/test';  

// Method 1
test('test login page', {  
tag: '@fast',  
}, async ({ page }) => {  
// ...  
});  

// Method 2
test('test full report @slow', async ({ page }) => {  
// ...  
});
```

``` bash
# run tests that have a particular tag with --grep command line option.
npx playwright test --grep @fast
# skip the tests with a certain tag:
npx playwright test --grep-invert @fast
# run tests containing either tag (logical `OR` operator)
npx playwright test --grep "@fast|@slow"
# run tests containing both tags (logical AND operator) using regex lookaheads
npx playwright test --grep "(?=.*@fast)(?=.*@slow)"
```

#### Group tests

You can group tests to give them a logical name or to scope before/after hooks to the group.
```js
import { test, expect } from '@playwright/test';  
  
test.describe('two tests', () => {  
	test('one', async ({ page }) => {  
		// ...  
	});  
	  
	test('two', async ({ page }) => {  
		// ...  
	});  
});
```

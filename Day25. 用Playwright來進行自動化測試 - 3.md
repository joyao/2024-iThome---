## Playwright Selectors

Element 選取器
通常會有以下selectors
- CSS Selectors
- Text
- ID
- Name
- Xpath

XPath可以支援很複雜的locate方式

``` js
// Text
await page.locator("text=Log in").click();
// CSS
await page.locator("button").click();
// Selecting Visible Elements
await page.locator("button:visible").click();
// Element Containing Element
await page.locator("article:has(div.promo)").click();
// Matching Conditions
await page.locator('button:has-text("Log in"), button:has-text("Sign in")').click()
// Selecting Elements Based on Layout
await page.locator('input:right-of(:text("Username"))').fill('value');
// Xpath Selectors
await page.locator("xpath=//button").click()
// ID, data-test-id
await page.locator('data-test-id=submit').click()
// N-th Element Selectors
await page.locator("button >> nth=0").click()
// Chaining Selectors
await page.locator("css=article >> css=.bar > .baz >> css=span[attr=value]").click()
```

範例網站: https://demoqa.com/
自動化測試可以寫成

今天要測 text-box
https://demoqa.com/text-box
![[Pasted image 20240907173308.png]]

```js
const { test, expect } = require('@playwright/test');

test.describe("Examples", () => {

    test("Testing Selectors", async ({page}) => {
        await page.goto("https://demoqa.com/text-box")
        await page.locator("#userName").fill("Test Username")
        await page.locator("[placeholder='name@example.com']").fill("test@gmail.com")
        await page.locator("#currentAddress").fill("This is the current address")
        await page.locator("#permanentAddress").fill("This is a permanent address")

        await page.pause()
    })

})
```

pause檢查

![[Pasted image 20240907173715.png]]

資料確實都有填入
再多加一行submit
``` js
await page.locator("button:has-text('Submit')").click()
```


Submit後會有以下資訊

![[Pasted image 20240907174003.png]]

## XPath
這邊就不贅述了，請直接看guru99的網站詳細解釋
https://www.guru99.com/xpath-selenium.html

![[Pasted image 20240907174203.png]]

## Locators Best Practices

以下網站提供了locator正確的範例，詳細講解了怎樣的Element應該用什麼locator抓取
https://playwright.dev/docs/best-practices


## Assertions

- assert 關鍵字可以測試，判斷條件回傳的是否為 `True`，如果回傳 `False` 的話，就會拋出一個 `AssertionError`。
- assertion是一種放在程式中的邏輯（如一個結果為真或是假的邏輯判斷式），目的是為了標示與驗證程式開發者預期的結果－當程式執行到斷言的位置時，對應的斷言應該為真。若斷言不為真時，程式會中止執行，並給出錯誤訊息。

https://playwright.dev/docs/test-assertions

接下來我們要用assertion去判斷我們上面送出的資料是否符合我們輸入的資料
因為有兩個一樣的id，所以會output會先抓output id再去抓底下element的ID

``` js
const { test, expect } = require('@playwright/test');

test.describe("Examples", () => {

    test("Testing Assertions", async ({page}) => {
        await page.goto("https://demoqa.com/text-box")
        await page.locator("#userName").fill("Test Username")
        await page.locator("[placeholder='name@example.com']").fill("test@gmail.com")
        await page.locator("#currentAddress").fill("This is the current address")
        await page.locator("#permanentAddress").fill("This is a permanent address")
        await page.locator("button:has-text('Submit')").click()

        const name = page.locator("#name")
        const email = page.locator("#email")
        const currentAddress = page.locator("#output >> #currentAddress")
        const permanentAddress = page.locator("#output >> #permanentAddress")

        await expect(name).toBeVisible()
        await expect(name).toHaveText("Name:Test Username")
        await expect(email).toBeVisible()
        await expect(email).toHaveText("Email:test@gmail.com")
        await expect(currentAddress).toBeVisible()
        await expect(currentAddress).toHaveText("This is the current address")
        await expect(permanentAddress).toBeVisible()
        await expect(permanentAddress).toHaveText("This is a permanent address")
    })
})
```

![[Pasted image 20240907180158.png]]

### 測試網頁
``` js
const { test, expect } = require('@playwright/test');

test.describe("Examples", () => {

    test("Testing Assertions", async ({page}) => {
        await page.goto("https://demoqa.com/text-box")

        await expect(page).toHaveTitle("DEMOQA")
        await expect(page).toHaveURL("https://demoqa.com/text-box")

    })
})
```

All pass
![[Pasted image 20240907180547.png]]

測試一個故意寫錯title
``` js
const { test, expect } = require('@playwright/test');

test.describe("Examples", () => {

    test("Testing Assertions", async ({page}) => {
        await page.goto("https://demoqa.com/text-box")

        await expect(page).toHaveTitle("DEMOQA_test")
        await expect(page).toHaveURL("https://demoqa.com/text-box")

    })
})
```
確實是failed
![[Pasted image 20240907180705.png]]


## Playwright Inspector 

可以利用以下指令開啟debug mode，就有dev tool可以debug

``` bash
npx playwright test --debug
```

或是在code裡面加
```js
await page.pause();
```


## 利用Test Generator來錄影測試

使用Codegen
``` bash
npx playwright codegen demoqa.com
```


左上角的record，會記錄你按的按鈕、輸入的東西，轉變成code
![[Pasted image 20240907181941.png]]

## 利用Playwright來下載檔案

[https://playwright.dev/docs/downloads](https://playwright.dev/docs/downloads)
![[Pasted image 20240910000957.png]]

``` js
const { test, expect } = require('@playwright/test');

test.describe("Example Tests", () => {

    test("Examples", async ({page}) => {
	    await page.goto("https://the-internet.herokuapp.com/download");
	    const [download] = await Promise.all([
		    page.waitForEvent('download'),
		    page.locator('text=some-file.txt').click(),
	    ]);
	    const path = await download.path();
	    const url = download.url();
	    console.log(path);
	    console.log(url);
    })
})
```

## 利用playwright來上傳檔案

[https://the-internet.herokuapp.com/upload](https://the-internet.herokuapp.com/upload)

![[Pasted image 20240910001350.png]]

``` js
const { test, expect } = require('@playwright/test');

test.describe("Example Tests", () => {

    test("Examples", async ({page}) => {
	    await page.goto("https://the-internet.herokuapp.com/upload");

		const [fileChooser] = await Promise.all([
			page.waitForEvent('filechooser'),
			page.locator('#file-upload').click(),
		])
	    await fileChooser.setFiles('uploadedFiles/sample.pdf');
	    await page.locator('input:has-text("Upload")').click();
	    await expect(page.locator('text=File Uploaded!')).toBeVisible();
	    await expect(page.locator('text=sample.pdf')).toBeVisible();
    })
})
```

## 利用playwright來產生PDF檔

![[Pasted image 20240910002434.png]]

``` bash
npx playwright pdf --viewport-size="1280,720" https://parabank.parasoft.com/parabank/services.htm sample.pdf
```

## Hovering Over 滑過顯示的測試

https://the-internet.herokuapp.com/hovers
![[Pasted image 20240910002618.png]]

``` js
const { test, expect } = require('@playwright/test');

test.describe("Example Tests", () => {

    test("Examples", async ({page}) => {
	    await page.goto("https://the-internet.herokuapp.com/hovers");

		await page.hover('[alt="User Avatar"]');
		await expect(page.locator('text=name: user1')).toBeVisible();
		await page.locator('text=View profile').first().click()
		await page.pause()
    })
})
```

## Auto-waiting 自動等待

[https://playwright.dev/docs/actionability](https://playwright.dev/docs/actionability)

Playwright 在執行操作之前會對element執行一系列可操作性檢查，以確保操作按預期的方式工作。
它會自動等待所有相關檢查通過，再執行請求的操作。如果在給timeout時間內未通過所需的檢查，則操作會顯示失敗並丟出 TimeoutError。

## Dialogs

Playwright 可以與 Web 對話方塊互相作用，例如alert, confirm, prompt 和beforeunload。

[https://playwright.dev/docs/dialogs](https://playwright.dev/docs/dialogs)

## 利用playwright安裝瀏覽器

![[Pasted image 20240910003444.png]]

``` bash
npx playwright install webkit
npx playwright install msedge
```


## NPX Playwright 一些設定

![[Pasted image 20240910003647.png]]

## 利用playwright來打開瀏覽器


``` bash
# Open website with webkit
npx playwright wk https://parabank.parasoft.com
# Open website with chromium
npx playwright cr https://parabank.parasoft.com
```


## Key press and shortcut 鍵盤事件

![[Pasted image 20240910004043.png]]

[https://the-internet.herokuapp.com/key_presses](https://the-internet.herokuapp.com/key_presses)

``` js
const { test, expect } = require('@playwright/test');

test.describe("Example Tests", () => {

    test("Examples", async ({page}) => {
	    await page.goto("https://the-internet.herokuapp.com/key_presses");

		await page.press('#target', 'F1')
		await page.press('#target', 'Delete')
    })
})
```

## 利用Playwright CLI來做螢幕截圖

![[Pasted image 20240910004328.png]]

``` bash
npx playwright screenshot -b webkit https://wikipedia.com wikipedia.png
npx playwright screenshot --full-page -b webkit https://wikipedia.com wikipedia.png
npx playwright screenshot --full-page --device="iPhone 11" -b webkit https://wikipedia.com wikipedia.png
```

![[Pasted image 20240910004651.png]]





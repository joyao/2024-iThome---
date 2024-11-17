
For functional testing, regression testing
可以寫程式也可以不寫，可以用它來寫test cases、執行test cases和分析你的測試結果。


https://katalon.com/

![[Pasted image 20240902224132.png]]

可以整合CI/CD, JIRA, GITHUB等
下載並安裝Katalon

開啟軟體
![[Pasted image 20240902224655.png]]

![[Pasted image 20240902224836.png]]


新增project

File -> New -> Project

MyFirstProject

![[Pasted image 20240902225034.png]]

![[Pasted image 20240902225220.png]]

Project -> Settings
![[Pasted image 20240902225424.png]]

Take Screenshot when execution failed

![[Pasted image 20240902225553.png]]

record & spy
![[Pasted image 20240902225822.png]]
- You record the steps and then execute them in spy


## Writing test case

![[Pasted image 20240902225933.png]]

![[Pasted image 20240902230011.png]]

https://katalon-demo-cura.herokuapp.com/
測試Katalon提供的sample網站

有兩種模式：Manual、Script
![[Pasted image 20240902230345.png]]

### 切換到Manual
Add
![[Pasted image 20240902230511.png]]
有很多action可以選

### 切換到groovy script

新增一行
``` java
WebUI.back()
```

![[Pasted image 20240902230700.png]]

### 再切回Manual

則會發現多了一個back action
![[Pasted image 20240902230801.png]]

所以這兩個是一樣的可以互通

### 開始撰寫

1. 移除掉現有所有Item
2. 新增open browser的action
   ![[Pasted image 20240902231110.png]]
3. Input
   url = https://katalon-demo-cura.herokuapp.com/
   ![[Pasted image 20240902231213.png]]
4. 執行 -> 確認初始化成功
   會自動打開頁面
   ![[Pasted image 20240902231440.png]]
5. 新增測試步驟
   這次使用Script示範
   `WebUI.verifyMatch(WebUI.getWindowTitle(), 'CURA Healthcare Service', false)`
   ![[Pasted image 20240902232006.png]]
6. 切回Manual檢查
   ![[Pasted image 20240902232029.png]]
7. 新增click action
   `WebUI.click(findTestObject)`
8. 利用spy web來選取物件
   ![[Pasted image 20240902232405.png]]
9. Mouse over navbar menu and send ALT + \` key and go to login option and go on
   ![[Pasted image 20240902232550.png]]
10. Change Object Name
    - SideHamburgerMenu
    - LoginButton 
      ![[Pasted image 20240902233856.png]]
11. 可以用Verify and Highlight來檢查是否有抓正確
12. Save
    ![[Pasted image 20240902233926.png]]
    
    ![[Pasted image 20240902234037.png]]
13. 將findTestObject改為 SideHamburgerMenu和LoginButton
    ``` groovy
    WebUI.click(findTestObject('Object Repository/Page_CURA Healthcare Service/SideHamburgerMenu'))
    WebUI.click(findTestObject('Object Repository/Page_CURA Healthcare Service/LoginButton'))
    ```
    ![[Pasted image 20240902234357.png]]
14. 新增close browser
    ![[Pasted image 20240902234501.png]]
15. 執行
    ![[Pasted image 20240902235005.png]]


### Adding test cases to test suites

1. Test Listeners -> New -> New Test Listeners
   ![[Pasted image 20240902235206.png]]
   ![[Pasted image 20240902235319.png]]
2. Listener Script
   ![[Pasted image 20240902235415.png]]
3. 將openBrowser的code移到 @BeforeTestSuite
	``` groovy
	/**
	 * Executes before every test suite starts.
	 * @param testSuiteContext: related information of the executed test suite.
	 */
	@BeforeTestSuite
	def sampleBeforeTestSuite(TestSuiteContext testSuiteContext) {
		println testSuiteContext.getTestSuiteId()
		WebUI.openBrowser('https://katalon-demo-cura.herokuapp.com/')
	}
	```
4. 將closeBrowser的code移到 @AfterTestSuite
	``` groovy
	/**
	 * Executes after every test suite ends.
	 * @param testSuiteContext: related information of the executed test suite.
	 */
	@AfterTestSuite
	def sampleAfterTestSuite(TestSuiteContext testSuiteContext) {
		println testSuiteContext.getTestSuiteId()
		WebUI.closeBrowser()
	}
	```
5. 檢視更改成果
   ![[Pasted image 20240902235928.png]]
6. 新增Test Suite
   ![[Pasted image 20240903000005.png]]
   ![[Pasted image 20240903000108.png]]
7. 將Navigation新增到test suite中
   ![[Pasted image 20240903000152.png]]
   
   ![[Pasted image 20240903000222.png]]

8. 執行test suite
   ![[Pasted image 20240903000430.png]]

## Take screenshot

在Test case最後新增一行

```
WebUI.takeScreenshot('screenshots/screen1.png')
```

執行test suite
![[Pasted image 20240903000944.png]]

可以從資料夾中找到screenshot
![[Pasted image 20240903001020.png]]

![[screen1.png]]

可以從Results看到測試結果
![[Pasted image 20240903001350.png]]


本文章同步發布於[個人blogger](https://hsujy.wordpress.com/)。
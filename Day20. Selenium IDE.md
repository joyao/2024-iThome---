
## Code less test automation

- 如果想要自動化regresssion test
	1. Codeless -> 較簡單，但不能跟開發自動化的功能相比
	2. Coded by writing code -> must have good experience in writing program language or automation scripts

- 使用selenium IDE

## Selenium 家族
![[Pasted image 20240831230450.png]]

- Selenium IDE是一個網頁瀏覽器 (Chrome, Edge, Firefox) 的外掛套件
- 他使用自動化的技術，像是record playback, capture replay
- 只要記錄下來你在網頁上操作的步驟
- Selenium WebDriver和 Selenium Grid兩個都比較進階

## 使用Selenium IDE來寫測試

Selenium IDE = https://chromewebstore.google.com/detail/selenium-ide/mooikfkahbdckldjjndioackbalphokd?hl=en-US&utm_source=ext_sidebar

Google web store search for selenium IDE -> install

![[Pasted image 20240831231014.png]]

Open

![[Pasted image 20240831231112.png]]

Record a new test in a new project

![[Pasted image 20240831231218.png]]

https://the-internet.herokuapp.com/
![[Pasted image 20240831231711.png]]

- Website: [Form Authentication](https://the-internet.herokuapp.com/login)

TC name = Login with valid user

![[Pasted image 20240831232828.png]]

點選 run all tests
![[Pasted image 20240831232825.png]]

![[Pasted image 20240831233316.png]]


如果手動，大約需要1分鐘，自動則30秒

點開log
![[Pasted image 20240831233810.png]]





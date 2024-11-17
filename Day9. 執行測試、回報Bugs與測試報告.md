
## Report Defects

defect reports 是由測試工程師寫的，但會送交給開發工程師
所以如果格式很混亂、缺少重要資訊或撰寫錯誤，這樣會有大問題

> Defect report is a documentation of the occurrence nature, and status of a defect.

defect = 問題 bug or fault
但並不是每個defect report都100%有defect，有時候是測試錯誤、或是測試環境錯誤等


### 1. Defect Report Title
- 不能太長也不能太短
- 格式:：Section -> Description
- 範例：Register -> No error message appears when user leaves password field empty

### 2. Steps to reproduce
- 必須要非常詳細
- 範例：
	1. Open xxx website
	2. Click on the hamburger icon in the upper left corner
	3. Scroll down to the bottom of the screen
	4. Click on Settings
	5. Click on data usage
	6. Change data usage to "minimum limit"
- 網路連線、打開瀏覽器這種不要寫進去，因為這是prerequesite，不是步驟

### 3. Expected Result
- 這個跟撰寫測項的expected result一樣


### 4. Actual Result
- 真實發生在執行測試步驟的結果


### 5. Test Environment
- 列出當defect發生時的環境
- 範例：
	- Windows 11 - Chrome - Ethernet - Development environment
	- MacBook pro M1 - Wi-fi
	- iPhone 11 iOS 13.3.1 5G Network - Production environment

### 6. Screenshot or Video
- 截圖必須要是全螢幕截圖
- 必須要用紅色框框要框出defect發生的地方
- 如果是影片，則滑鼠點下去的動作必須要顯示出來
	- 電腦 Click
	- 平板手機 Tap

### 7. Defect priority
- Critical：不能登入、軟體crash
- High：登入網站回應很慢、使用者不能新增照片
- Medium：有些網頁效能很差、Portrait模式沒辦法很好的運作
- Low：拼音錯誤、照片沒對齊

但以上這些不是絕對，還是要取決於系統設計

## Types of Defects


### 1. Functional
- 一些功能沒有作用

### 2. Visual (UI)
- 版面跑掉

### 3. Content
- 內容重複

### 4. Performance
- 影片花太多時間載入

### 5. Suggestion
- 並不是Defect，但是一個建議可以讓系統更好
- 字體大小應該要大一點


## Example defect report

![[Pasted image 20240816225742.png]]


## 利用tool撰寫defect report


## 截圖

Tool: ScreenPal

https://screenpal.com/

## Web logs

這也是一個很重要該付上的檔案
不是必需的，但對於開發者來說有Log解defect比較方便
(尤其在BIOS)


## Defect Lifecycle

![[Pasted image 20240816235029.png]]

https://www.geeksforgeeks.org/bug-life-cycle-in-software-development/

![[Pasted image 20240816235421.png]]

## Accessibility defects

- 確保你的系統是可以適用在各種不同的人身上
- 看不到、聽不到、無法說話、行動障礙等
- 但這區塊比較難也較少
- Axe accessibility testing tool

## 測試報告 Test Report

## 誰是聽眾?

這份報告是要給誰看的? 工程師? 主管? CEO? 還是PL? test leader?


### Types

- Test Progress report: 定期的測試報告，又稱為test status report
- Test Completion Report: 測試結果報告
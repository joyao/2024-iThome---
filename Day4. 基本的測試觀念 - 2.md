
## Test Levels 測試階層


![[Pasted image 20240810151312.png]]

分成
- 單元測試
- 整合測試
    - 元件整合
    - 系統整合
- 系統測試
- 驗收測試
    - Alpha 測試
    - Beta 測試

### Unit testing 單元測試
- 關注在每個funciton，每個元件上的測試，可以是code的classes、interface
- 是開發者的工作

### Integration Testing 整合測試
- 分成兩類 component integration、system integration
- 元件和元件之間的測試，稱為整合測試

#### Component Integration 元件整合
- 兩個class之間的相互作用
- 也是需要跑code才能完成
- 所以主要是developer開發

#### System Integration 系統整合
- 兩個系統間的測試
- ex. DB和API、前端和後端
- 這個不是從component integration來的
- 可以是測試人員執行
- 是Optional的，因為不一定每一個Project都有兩個系統，像是單一一個資料處理的程式就沒有


### System testing 系統測試
- 主要是由測試人員執行
- 主要由stakeholder再發布要release的決定後開始執行
- 測試環境必須跟正是環境類似
- 主要目標是找到defects、增加品質


### Acceptance Testing 驗收測試
- 關注在於整個系統或產品的behavior和capanbilities
- 不應該是找到defect、應該是bug-free
- 用來建立信心、測試產品確實可用
- 像是Alpha testing & Beta testing，主要取決於目標和用戶

#### Alpha testing
- 邀請一些淺在客戶或用戶，在監督下在公司進行測試
- 像是security concern

#### Beta Testing
- 主要用在遊戲和apps
- 邀請制的測試，可以監控效能、產出報告




---

## Testing Types 測試類型

分為
- 功能性測試
- 非功能性測試
- 黑箱測試
- 白箱測試
- 動態測試
- 靜態測試
- 驗證測試
- 回歸測試
- 煙霧測試

### Functional Testing 功能測試
- 例如登入
- 有沒有輸入帳號密碼、輸入不合理的帳號密碼、輸入很長很短的字串
- 只會有yes/no的答案

### Non-functional Testing 非功能性測試
- 測試系統如何運作
- 包含usability, performance, security
- 很難回答是否正確、只能回答一個範圍
- 像是按下按鍵後，多少秒數才合理 (BIOS開機?!)
- 通常是整理資料後，將資料提供給負責人去決定是否合理
- 像是Benchmark標準、業界市場的標準、或是國際標準


### Black-Box Testing 黑箱測試
- 提供Input資料、但你不知道裡面如何運作、但可以驗證輸出資料是否正確
- 對於大多數測試人員來說 有80%都是黑箱測試
- 假設如果系統比較不穩定、就比較需要增加白箱測試
- 假設是一個簡單的程式、則使用黑箱測試就好

### White-Box Testing 白箱測試
- 有權限可以看到code
- 主要測試functionalilty
- API傳了什麼資料、收到什麼資料
- 需要有開發語言的基礎
- 可以找到在黑箱測試找不到的defects


### Dynamic Testing 動態測試
- 任何只要有input output的測試都是動態測試
- 不管他是黑箱還白箱測試都是動態測試

### Static testing 靜態測試
- 不需要執行軟體的測試
- 像是review需求、review設計、甚至是review code

### Retesting (Confirmation testing) 驗證測試
- 去測試修正後的code來驗證是否已經確實修復
- 測試相同的function

### Regression Testing 回歸測試
- 去測試debug沒動到的程式，但可能會因為debug後而造成錯誤
- 主要用自動化測試去跑，因為需要跑非常大量的測試、尤其是release的時候
- POT test


### Smoke Testing 煙霧測試
- 有非常多版本的程式
- 在我測是新版的程式之前，先建立一些非常簡單的測試
- 像是登入、加入購物車、購買、登出整個流程
- 如果通過了，才會開始測試更深入的流程
- 如果連這麼簡單的測試都過不了、那後面就不用測了、直接reject
- 告訴開發人員 你連這麼簡單又基本的都過不了，我不想側了、你直接拿回去改過、沒改好之前我是不會測其他的
- 用這種測試主要是節省時間
- 如果要整個run過全部的基本的測社要4、5小時，例如無法結帳，無法讓你做接下來的事情，這樣可能已經過去2天了 才叫開發人員去解決
- 當他在解決的時候取消測試



ISTQB


什麼是測試？
- 很多人都有遇過你開發的軟體實際跑起來並不符合自己想要的功能、模式
- 造成金錢上的損失、浪費時間與商業的受損 (security threats)
- 軟體測試是：
	- 增加軟體的品質
	- 減少軟體執行錯誤的風險 (省錢、省時間)
	- 軟體測試不是只有測試而已，是一個流程包含了很多的步驟，執行軟體測試只是其中的一小部分


軟體測試可以分為動態測試和靜態測試

## Dynamic Testing 動態測試 (TBD)
- 必須要跑code
- 必須要執行在機器上，並且得到結果

## Static Testing
- 不包含任何流程
- 不要求Input, output
- Figma design and review，review requirement，拿到設計文件、從設計文件中去分析出需要測試的部分
- code review也是其中一種測試 (是否有符合rule、是否有寫好註解)
- 最重要的點：Early testing saves time and money
- 是一個最簡單的測試方式
- V-model left part
- 從開發軟體的第一天開始就要導入
- 有可能static和dynamic是同時出現的


另一個軟體測試的分類可以分成兩種：Validation and Verification

## Verification 驗證

- 是否有沒有符合需求 ex. 正常登入
- 功能、規格是否正常
- White box testing

## Validation 確認
- 需求是否是客戶要的
- 是否符合客戶的期望
- 主要著重在使用者、市場體驗
- Acceptance testing

https://fivevalidation.com/verification-validation-vv/

![[Pasted image 20240810122450.png]]

https://www.geeksforgeeks.org/software-engineering-verification-and-validation/

![[Pasted image 20240810121741.png]]


## Objectives of Testing

![[Pasted image 20240810122735.png]]


Preventing defect: review design

providing info to stakeholder: 
	internal : to project manager
	external : development for another company


## Testing & Debugging

測試是用來找到問題或錯誤、寫一個報告
而debuging是要了解問題、嘗試去分析他的code，來解決這個defect
debugging不是只有developer來完成，因為如果這個defect是介面設計上的問題的話，那designer就要去解決；如果這是需求問題，那就要請business analyst去解決
解決完問題以後，會有confirmation testing 驗證測試，測試這個defect是否真的被解掉了。在這個階段，會重複之前發現問題的測試步驟，確保真的解掉了
如果被解掉了，就關掉ticket，但如果沒有被解掉，就回到debugging的步驟

其實debugging後，有兩種測試，一種是confirmation testing (測試同個領域的)，另一種是regression testing

regression testing 是用來測試那些我們debugging沒有改到的功能，但可能會被改到的功能影響到的



## Test process

測試的步驟主要分成三個步驟
1. Plan - 分析、擬定規範、計畫、工具
2. Design - 設計測試案例、情境、環境
3. Execution - 執行測試、輸出測試報告


## Test process Activities

![[Pasted image 20240810144202.png]]

![[Pasted image 20240810151142.png]]


本文章同步發布於[個人blogger](https://hsujy.wordpress.com/)。

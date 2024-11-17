這篇列了一些面試測試工程師可能會有的題目，但因為版面關係只列出少部分基本的


## Q1. SDLC和STLC的差異?

SDLC - Software Development Life Cycle
STLC - Software Testing Life Cycle


都是Life Cycle，但SDLC主要在講軟體開發的生命週期、STLC主要在講軟體測試的生命週期

SDLC 主要在於開發出高品質的軟體，且該軟體是符合客戶要求和時間、成本的
SDLC有兩種不同的流程
- Sequential Life Cycle - Waterfall Life Cycle, V model
- Incremental Life Cycle - Scrum, Agile ...

STLC - 主要為測試的流程、由測試團隊來去確保軟體或產品的品質，是SDLC的其中一項，但它只有測試的階段
在V model的右半邊


## Q2. 不同階段(Phase)的軟體測試有哪些?

### Unit Testing
- 主要為驗證軟體的每一個功能是否正常運作，跟資料是不相干的，單純只測功能
- 應為開發工程師來開發

### (Component) Integration Testing
- 主要為測試unit和unit之間的的相互作用是否正常運行、正常結合
- 可以抓出互相作用有誤的情形
- 應為開發工程師來開發

### System Testing
- 主要為測試整個系統的運作，來確保整個產品都有依照規劃正常運作
- 應為測試工程師來執行

### System Integration Testing
- 若有兩個系統，像是前端與後端、API和Database，這時候應該就要做system integration testing
- 應為測試工程師來執行

### Acceptance Testing

- 主要不是要去找defect，而是要去確保軟體是可以準備提供給客戶使用
- 主要為是否符合使用者的需求、是否已經可以發布了
- - 主要由stakeholders來執行 (ex. Users)
- 像是Aplha Testing, Beta Testing, contract and regulatory acceptance testing, operational acceptance testing, user acceptance testing
- UAT, OAT


## Q3. Test case和test scenario的差異

### Test scenario

- 任何一個功能都可以被測試、去找出需要被測試的項目
- 又可以稱為test condition 或 test possibility

### Test case
- test case是一系列的步驟來去執行驗證特定的feature或功能有沒有正常運作
- 所以它是包含actions的
- 但有些action像是expected result和actual result 不會被填寫直到我要執行測試
- 包含
	- test steps
	- test data
	- precondition
	- postcondition
	- expected result
	- actual result

如果不通過，就要寫defect report


## Q4. functional 和non-functional testing的差異

不同Type的testing，只要問到不同"Type"，就是這兩個

### Functional testing

- 是一種測試用來驗證每個軟體的function都有正常運作且符合規範，使用來測試系統的作用的

### Non-functional testing
- 是用來測試一些非功能的測項，像是performance, usability, reliability
- 用來測試系統的性能
- 這個測項沒有對或不對的這種絕對值，只有一個Range


## Q5. Validation和verification的差異

### Validation
- Are we building the right product?
- 客戶是否滿意系統、軟體
- 客戶的觀點
- 可以使用functional testing, system testing, regression testing 等方式
- Validated by executing the software code

### Verification
- Are we building the product right?
- 功能是否正確符合規範
- 從開發者的觀點去看
- Verified without executing the software code
- 為review的techniques
- 主要使用靜態的測試


## Q6. 我們在執行計畫中什麼時候要開始測試

- 應該要在軟體開發的前期就要納入測試考量 (ex requirement gathering and design phase)
- 前期就納入考量可以解少defect的數量和rework的數量
- "Early testing saves time and money"  (and reputation)


## Q7. 如果我們沒有很清楚的使用者需求，我們要怎麼測試軟體

1. 去盡可能蒐集可以蒐集到的文件，盡管是少量的也可以
2. 使用舊版或是現在版本的系統當作對照去測試新版本的軟體產品
3. 跟計畫團隊成員討論
4. 使用exploratory testing來測試已經完成的系統  (解釋什麼是exploratory testing)


## Q8. 什麼是exploratory testing

- 是一種軟體測試方式 that is concisely describe as simultaneous learning test design and test execution.
- 如果沒有時間做一個完整的正式測試，則使用exploratory testing是一個很好的方式
- 測項不是事前就建立的 but testers check system on the fly.
- 用於兩種理由：
	1. 如果我們沒有時間去設計test cases
	2. 如果很窮或是沒有需求

## Q9. 什麼是change-related testing? 為什麼我們要用它? Confirmation testing和regression testing的差異?

Change-relate testing是用來在系統變更的情形上的，而軟體的變更會需要兩種測試

### Confirmation testing、re-testing
- 看defect是否有正確解掉了

### Regression testing
- 為了避免解defect的時候影響到其他已存在的feature，所需要做的全面性的測試
- impact analysis is used to know how much regression testing will be required.


## Q10. 黑箱測試、白箱測試與灰箱測試的差異

### Black-Box testing
- 用來測試那些測試人員不知道的系統架構、設計和實作的項目

### White-Box testing
- 用來測試那些測試人員知道的系統架構、設計和實作的項目

### Gray-box testing
- 只有部分知道內部的架構後系統
- 用來搜尋和找出因為不適合的程式架構和使用方式而測試找到defect
- Use postman


本文章同步發布於[個人blogger](https://hsujy.wordpress.com/)。
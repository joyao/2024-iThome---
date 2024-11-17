

## 什麼是黑箱測試?

你必須要給輸入資料，等待系統的處理並等待輸出資料，中間怎麼處理的你不會知道，這就是黑箱測試

灰箱測試 Gray-box - Partial access to the system
- API Testing
- DB Testing

有些人會覺得上述是白箱測試、但有些人覺得是灰箱測試


- 通常黑箱測試是用在system testing 和 acceptance testing
- 我們不會知道系統內部是怎麼處理的，我只要知道我給了input而output符合我的預期
- 有些人說這是 behavior-based testing

## 5個黑箱測試重點

1. Equivalence Partitioning
2. Boundary Value Analysis
3. Decision Table Testing
4. State Transition Testing
5. Pairwise Testing

## Equivalence Partitioning (EP)


目標，用一個test case來cover每一個partition 
1. 定義你的partition (可以將你的待測內容切成好幾個分區)
2. 每個Partition每次至少測試一次
3. 達成100% Equivalence Partitioning coverage
4. parition可以是年齡、金額、時間、分類 等
### Example

![[Pasted image 20240814231914.png]]

右下角為test case


## Boundary-Value Analysis (BVA)

是 Equivalence Partitioning 的延伸，所以如果有做 Equivalence Partitioning，也可以做Boundary-Value Analysis 

Equivalence Partitioning 比較簡單
如果你的系統比較複雜，那應該要選擇Boundary-Value Analysis

但要做Boundary-Value Analysis 的話你的系統的每個partition必須要有非常明確地開始和結束邊界

![[Pasted image 20240814233527.png]]

這時候會測4:59 和5:00  & 6:59 和 7:00
最重要的目標是要測試前一個partition和現在的partition
工程師可能在寫程式的時候忘記加了 等於，導致邊界值會錯誤

需要花比較多時間去設計和執行測試

## Summary for EP and BVA
1. 每個值都只屬於一個Partition
2. EP和BVA都可以用在input和output的值  (有些是輸入會有區分、有些是輸出msg會有區分)
3. 會有兩種類型的Partition -> valid and invalid (不是只有測可以過的值)
4. (EP) Number of partitions covered by test cases divided by total number of partition
   ex. 如果有10個partition，但你只有5個TC，那我的equivalence partitioning   coverage是50%
5. (BVA) Number of boundaries covered by test cases divided by total number of boundaries
   像是4:59和5:00這樣算是2個boundaries，而不是一個 
6. 在有些測試，要達成100%是不可能的，但對於EP和BVA，是應該Should  要達到100%才對
7. 如果測試兩個值在同一個parition裡面，並不會增加coverage !!! (重要)


## Decision Table Testing

不同的條件組合會有不一樣的結果

ex. 要買大於100元的物品，並且也有金牌會員，才能有折扣
建一個True False table

n個條件會有2^n個table rules



## State-Transition Testing

是一個有先後順序狀態和path的測試

### Example
![[Pasted image 20240815002057.png]]

是不可能將所有state都在同一個test case中測試 ex. EF不可能放在同一個test case
所以以這種情形，需要4個 test cases才能 cover (DEFC)

## Pairwise Testing
- 為一項技術可以用一些特殊測項測你的網頁或app

假設你有個表單，每個欄位都有好幾個不同選項或值，這樣要如何測試?
Each pair of values should appear with each other at lease in one test case.
像是多條件的篩選 排列組合下會有超多的test cases

可以不用自己手動去產生測試，有tool
https://pairwise.yuuniworks.com/

### Example

![[Pasted image 20240815003412.png]]


- `5*7*2*3*2 = 420` 個測項，千萬不要嘗試
- 兩兩一組，只要有cover 到就好了，不用每個條件都要列出來
- 常用在一些有很多按鍵的產品的軟體測試

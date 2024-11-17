
測試工程師大部分都是agile team的其中一員
數據說明目前至少80%的軟體開發團隊都是 agile 團隊 (這句我很懷疑拉，畢竟我認識或經歷過的團隊都不太走真正的agile，只是表面上而已

所以這篇我們主要的目的為：
1. 了解agile的知識
2. 用tool去實現

Sequential -> project run sequentially
Cone of Uncertainty

執行agile不會有很大量的工項與不確定性、且不給太大的承諾後才進行

總共有 4 rules & 12 principles

---

## 4 Rules

### 1. Individuals & Interaction Over Processes & Tools

- 主要強調測試工程師之間的關係與測試和開發人員的關係和互動

### 2. Working Software Over Comprehensive Documentation

- 有一個working software 比起單有文件來的好

### 3. Customer Collaboration Over Contract Negotiation

- 在開發過程中跟客戶合作更改設計確保符合客戶要的，超越合約

### 4. Responding to Change Over Following a Plan
- 依照計畫執行並不是最重要的事情，最重要的是依照計畫並納入變更
- 擁抱變更
- 計畫非常彈性


principles are above rules

## 12 Agile principles

1. Our highest priority is to satisfy the customer through early and continuous delivery of valuable software
2. Welcome changing requirements, even late in development. Agile processes harness change for the customer’s competitive advantage.
3. Deliver working software frequently, from a couple of weeks to a couple of months, with a preference to the shorter timescale.
4. Business people and developers must work together daily throughout the project.
5. Build projects around motivated individuals. Give them the environment and support they need, and trust them to get the job done.
6. The most efficient and effective method of conveying information to and within a development team is face-to-face conversation.
7. Working software is the primary measure of progress.
8. Agile processes promote sustainable development. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.
9. Continuous attention to technical excellence and good design enhances agility.
10. Simplicity–the art of maximizing the amount of work not done–is essential.
11. The best architectures, requirements, and designs emerge from self-organizing teams.
12. At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behavior accordingly.


## Agile和waterfall的開發差異

![[Pasted image 20240820201514.png]]

https://www.process.st/waterfall-vs-agile/


## Whole team approach

- 整個團隊對所有事情都要負責
- agile團隊需要包含所有需要的人 (不同角色的)
- 小團隊 3~9人
- 團隊是需要co-loacted，在同一個地區、分享同一個工作空間
- 品質是所有工程師的責任

### 測試者的角色
- 和business representative合作來幫他們建立合適的acceptance tests
- 和開發人員合作來同意測試策略和決定自動化測試的方法
- 轉移和增加測試的知識給別的團隊成員，並且影響產品的開發


### Power of Three
- 測試人員、開發人員和business representative在全部都功能討論上都需要餐與



## Early & Frequent Feedback

- 提前並密集地知道客戶的回饋與要求，互相sync想法，減少未來接近完成時才更改的成本

### 好處

- 避免誤會需求，可能會造成延後發現問題，增加更改的成本
- 清楚了解客戶的功能需求，並且讓客戶提前體驗，這樣才能有更好的客戶所需要的功能的回饋
- 提前發現、釐清、解決品質問題



## User Story

- User story 是用來了解從開發者、測試者和business representative的角度來看的需求。必須要包含functional和non-functional的角色。

![[Pasted image 20240820203234.png]]

## Decomposing Requirement

User story不是唯一一個在agile內的格式

共有5種type

有一個大需求，需要分解成小需求

### Themes
- 主要大方向
- 會往下分解成一個或多個epics
- 每一個產品roadmap可能會有一個或多個theme

### Feature
- Feature比epics和User story還大
- 是一個可能提供給客戶的功能
- high level

### Epic User Stories
- 中型的需求，是從feature降解下來的

### User stories
- 包含"一個"action的需求


### User Tasks
- Actions 用來開發一個user story的需求

並不是每個agile的案子都有符合這5種type

本文章同步發布於[個人blogger](https://hsujy.wordpress.com/)。
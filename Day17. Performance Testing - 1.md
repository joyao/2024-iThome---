
是一個很重要的測試流程，試想假設有1000人同時使用系統，會造成甚麼影響

## What is performance Testing

- Time behavior
	- 回傳資料時間
- Resource Utilization
	- allocation of limited RAM
- Capacity
	- numbers of users or volumes of data

- 是一個包含了任何跟performace或responsiveness有關的測試


## Type of performance testing


- Load Testing
	- 著重在當有現實真的可能達到逐漸增加的多個人或多份資料要進行載入，要如何控制
- Stress Testing
	- Focuses on the ability of a system or component to handle peak loads that are at or beyond the limits of its anticipated or specified workloads.
	- 如果Load testing 是100,000人，則stress testing可能要測300,000人、500000或1百萬
	- 長時間的測試
- Scalability Testing
	- Focuses on the ability of a system to meet future efficiency requirements which may be beyond those currently required.
	- 可以增加memory嗎、可以增加容量嗎
- Spike Testing
	- 類似Stress Testing
	- 測試在突然來的尖峰時期也可以回覆正確的資料
	- 短時間的測試
	- ex. 奧運、FIFA等網站
- Endurance Testing
	- 一段長時間內，系統所能承受的流量
	- 像是筆電的app之類的，需要長時間開啟，因為大多數人不會關電腦、是否會造成問題
- Concurrency Testing
	- focuses on the impact of situations where specific actions occur simultaneously
	- 當大量的使用者在同時間登入
	- 跟spike testing很像
- Capacity Testing
	- 有多少user或是transaction系統可以承受且執行正確


## Load generation

怎麼樣產生這些流量資料，方式：

- User interface - 我們需要一些人，just small group of people
- Crowds - 需要大量真實的使用者來access系統，好處是可以有不同地區的人進行測試，但很花錢、也會有security concern，因為太多人都可以用你的系統
- APIs - This is less sensitive to change in the UI. 沒辦法測試到UI的畫面
- communication Protocols - 使用tool來模擬非常大量的使用者. ex. JMeter

## Creating Load Profiles


- Operational profile是使用者可能在系統上會有的舉動
	- 例如上班打卡的時間是9點、下班打卡是6點，這種就是behavior他們會在系統上做的事情
	- 例如主管主要在10點開始去解決簽核的事情
- 依據OP我們可以建立我們的Load profile
- Load profile 指的是一個component或系統被測試的這個動作可能會跟實際情形有關
	- 合併上述好幾個Operation profile來建立load profile，利用testing tools去執行測試


Create a correct load profile:
- Performance Testing待測試項目
- 建立OP來表示不同的使用情境
- OP執行在每個SUT上，期望的時間和數量
	- Ramp-ups: Steadily increasing load (add one virtual user per minute)
	- Ramp-downs: Steadily decreasing load
	- Steps: instantaneous changes in load (add 100 virtual users every five minutes)
	- Predefined distribution: (volume mimics daily or seasonal business cycles)

Load profile examples:

Load profile 1
![[Pasted image 20240827234708.png]]

- Consist step input of 100 virtual users.
- Represent a background load.

Load profile 2
![[Pasted image 20240827234807.png]]

- Consist of  a ramp-up to 220 virtual users that is maintained for two hours before ramping up

Load profile 1 + 2
必須要結合兩個，因為使用這並不會分開使用

![[Pasted image 20240827235041.png]]

- 主要目標為3小時的stress test


怎麼使用測試tool並不是很重要，最重要的是要怎麼樣才能有正確的load profile


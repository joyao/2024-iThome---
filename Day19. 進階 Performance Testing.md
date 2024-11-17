
## Response Time
- 應用程序的回應使用者需求的時間

### Absolute Response Time
- 從使用者按下連結到伺服器回傳完整資料的整個時間

### Perceived Response Time
- 使用者接收到資訊的時間
- 有時候一個網站非常複雜，使用者可能會需要非常長的時間才能接收到資料，這時候工程師可能會把他切分成好幾個request和response，排序進行。
- 這時候可能有部分的已經收到資料先展示給使用者，而剩下的則繼續執行接收。這時候absolute response time可能是10秒，而Percerived Response Time也就是使用者看到頁面，可能會是1秒，但並沒有100% ready

### Rendering Time
- 瀏覽器從server接收到資料後，處理和渲染頁面的時間
- 這取決於網頁的複雜度

### Network Latency
- 資料封包透過不同設備獲取、傳遞、處理的網路延遲時間
- 會依據不同的設備而有不同
- 線上遊戲不能超過100 milliseconds，但最好是20ms~40ms


### Throughput
- 一個單位時間內，資料傳遞的數量
- 通常以 transactions/second 或是 bandwidth (bytes/seconds) 來表示


### Utilization
- 最大流量的比例
- 不建議超過80%，如果超過，建議使用load balancer分流


### Robustness
- 這個系統對應系統不同錯誤或例外的能力
- 假設今天系統沒有辦法承受突發流量而造成的錯誤，當我移除掉突發流量後，是否系統還能會到原本的狀態繼續執行
- 使用MTBF (Mean time between failure)來評估系統的Robustness


## Performance Test 的環境
- 硬體與軟體設備需要被使用在performance test
- 不建議在線上系統上操作，應該要建一個測試環境

### 為什麼要建立測試環境
- The system might crash
- 應用程式反應時間會比較快
- 可能會因為使用測試帳號而造成安全漏洞
- 線上系統的資料庫可能會有測試的input/output資料
- 軟體的log fils和system log file可能會被測試填滿
- Analytics資料會被影響 

- performance的環境應該要跟線上環境非常像
	- 但有可能會造成需要多花非常多錢，因此有一些會只有建立部分的環境。像是原本可能需要4台sever，我可以使用1台就好，預期他可能有1/4的效能
- Performance的環境必須要被隔離，例如雖然我的環境跟正是環境部一樣，但我們都架在同一台server上，這樣就沒有做到隔離

## Serial Execution of Thread Groups

1. 建立一個test plan叫 Serial Execution
2. 新增兩個thread group: Group A, Group B

![[Pasted image 20240828215646.png]]

3. 在Group A和Group B 中新增 Sampler -> HTTP Request


### Group A

![[Pasted image 20240828220133.png]]

Name:  Nokia lumia
Protocol: https
Server Name or IP: www.demoblaze.com
Path: prod.html?idp_=2

![[Pasted image 20240828220745.png]]

### Group B
![[Pasted image 20240828220150.png]]

Name:  Samsung galaxy
Protocol: https
Server Name or IP: www.demoblaze.com
Path: prod.html?idp_=1

![[Pasted image 20240828220552.png]]



Add listener -> View Results Tree

執行測試三次
![[Pasted image 20240828220836.png]]

![[Pasted image 20240828220818.png]]

設比較大的值

![[Pasted image 20240828221149.png]]

就會發現它執行並沒有先後順序
![[Pasted image 20240828221245.png]]

新增listener -> Aggregate Report

重跑一次

![[Pasted image 20240828221526.png]]

如果我們把Serial Execution -> Run Thread Group consecutively (ie. one at a time) checked

![[Pasted image 20240828221706.png]]

會發現它會一個一個照順序跑


## 使用者自訂義參數

再加一個  Sony xperia

Name:  Sony xperia
Protocol: https
Server Name or IP: www.demoblaze.com
Path: prod.html?idp_=6

![[Pasted image 20240828222210.png]]

這時候如果我們今天要改Server Name或IP的時候就會非常麻煩

從 Serial Execution裡面去 Add variable

- produrl = www.demoblaze.com
- testurl = test.demoblaze.com

![[Pasted image 20240828222551.png]]

回到原本的 把全部值都改參數

Server Name or IP = ${produrl}
![[Pasted image 20240828222750.png]]

![[Pasted image 20240828223046.png]]

## Action After Sampler Error

ex:
![[Pasted image 20240828223332.png]]

可以看到就算error了還是繼續執行

因為我們在Thread group有選 Action to be taken after a Sampler error -> Continue

將Sony移到Group A，並移除Group C

如果我們把Group A設為以下值
Action to be taken after a Sampler error -> Start Next Thread Loop

![[Pasted image 20240828223733.png]]

Nokia錯誤了就不會執行Sony

Group A loop count = 2
![[Pasted image 20240828224240.png]]


Action to be taken after a Sampler error -> Stop thread
![[Pasted image 20240828224419.png]]

Action to be taken after a Sampler error -> Start Next Thread Loop
Loop Count = Infinite

![[Pasted image 20240828224750.png]]

Action to be taken after a Sampler error -> Stop thread
Loop Count = Infinite

![[Pasted image 20240828224817.png]]

Action to be taken after a Sampler error -> Stop Test
Loop Count = Infinite
![[Pasted image 20240828224927.png]]

Action to be taken after a Sampler error -> Stop Test Now
Loop Count = Infinite

![[Pasted image 20240828225043.png]]


## Controller

### Simple Controller
- 像是資料夾儲存你的request
- 可以用分頁或網站的nevbar來區分不同的sampler
- Add -> Logic Controller -> Simple Controller
- 可以加Listener進Controller
- 但只有thread group可以設定執行人數、controller不行，但controller可以分開測試結果的報告


### Loop Controller

- Add -> Logic Controller -> Loop Controller
- 可以設定loop count

### Runtime Controller
- Add -> Logic Controller -> Runtime Controller
- 可以設定執行的時間 -> Runtime 60 secs
- 不是設定次數，而是設定時間看能測幾次

### Throughput Controller
- Add -> Logic Controller -> Throughput Controller
- 可以設定Based on Percent Executions 或 Total Executions
- 設定Throughput ex.1.0
- Total Execution 表示全部只會跑5次
- 若是整個thread Group設定跑100次、Percent Execution設定5%，則總共會跑5次

### Once Only Controller
- Add -> Logic Controller -> Once Only Controller
- 只執行一次
- Ex. 註冊、登入

### Interleave Controller
- 一次只跑一個request
- 但是是照順序跑的
- 假設這個controller下有ABC三個sampler。這次跑A、下一個loop跑B、再下一個loop跑C
- ex. 測試不同的user role



## JMeter

https://jmeter.apache.org/

下載最新版的.zip
並在bin裡面找到jMeter.bat並打開

![[Pasted image 20240828000557.png]]

![[Pasted image 20240828000611.png]]

### Thread Group


Create a tread group
![[Pasted image 20240828000758.png]]

Name: Users
Number of Threads (users): 10
Ramp-up period (seconds): 120
Loop Count: 10
Specify Thread lifetime: checked
Duration (seconds): 60
Startup delay (seconds): 10

![[Pasted image 20240828001218.png]]


### Use sampler
![[Pasted image 20240828001350.png]]


![[Pasted image 20240828001906.png]]

![[Pasted image 20240828001919.png]]

執行
但這個並非是一個很好的測試方式


### Listeners

Add View Results Tree, View results in table


![[Pasted image 20240828002141.png]]

![[Pasted image 20240828002254.png]]

再執行一次Request

#### View Results Tree

![[Pasted image 20240828002440.png]]


#### View Results in Table
![[Pasted image 20240828002527.png]]


## BlazeMeter

https://www.blazemeter.com/

Install google chrome extension
https://chromewebstore.google.com/detail/blazemeter-the-continuous/mbopgmdnpcbohhpnfglgohlbhfongabi?hl=zh-TW&pli=1

![[Pasted image 20240828003033.png]]

![[Pasted image 20240828003722.png]]

打開測試網站：https://blazedemo.com/
![[Pasted image 20240828003534.png]]

start recording

更改值
![[Pasted image 20240828003934.png]]
先新增步驟再動畫面

Save
![[Pasted image 20240828004753.png]]


Open JMeter

File -> Open

![[Pasted image 20240828005040.png]]

### Add listeners

- Aggregate Report
- Summary Report

![[Pasted image 20240828005719.png]]

![[Pasted image 20240828005731.png]]



## Average vs Medium

Example 1:
100, 1000, 2000, 3000, 100000

Average = (100 + 1000 + 2000 + 3000 + 100000) / 5 = 21220 -> failed
Median = 2000

Example 2:
10, 10, 10, 10, 1000, 9000, 2000

Average = (10 + 10 + 10 + 10 + 1000 + 9000 + 2000) / 7 = 5148
Medium = 10 -> failed
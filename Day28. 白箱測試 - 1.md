
## 什麼是白箱測試

白箱測試就是Program裡面如何運作的是透明的可見的

主要用來測底下幾個測試類型
- Architectural testing
- Structural testing

主要使用人員類型
- Developers
- Testers in critical system
- Team cross functionality

## 白箱測試的方法
- Statement Coverage
- Decision Coverage
- Condition Coverage
- Path Coverage
- MCDC
- others


## Statement Coverage

Statement指的是任一一行code
而statement coverage的目標是覆蓋所有code的statements，得到100%的statement coverage

Statement Coverage = no. of statements tests / total no. of statements

### Example 1
```
if x > 7:
	print "hello"
```

#### statement test 1:
x = 8
當給予x = 8時，會執行到所有的code，這時候就是100%的覆蓋率
#### Statement test2:
x = 5
當給予x=5時，只會執行第一行，這時候為50%的覆蓋率

### Example 2

```
if x == 3:
	print "hey"
else:
	print "never mind"
```

#### Statement test:
在這個案例，沒辦法只使用一個test case就完成100% statement coverage，必須要至少兩個
x = 3, x= 5 達到100% Statement 覆蓋率


### Example 3

```
if day == "Monday"
	then statement a
else
	statement b
end if
if day == Tuesday
	then statement c
end if
```

#### Statement test:
這種情形有很多的測試選擇，且沒有辦法用很少數的測項達到100%覆蓋率
至少會有兩個test cases
1. day = Monday
2. day = Tuesday

### Example 4

```
Start
Do until B == C
	if today == Monday
		set A=1
	else if today == Wednesday
		set A=2, B=C
	end if;
	if B < C
		B = B + 1
	end if;
end loop
end
```

#### Statement test:
至少會有兩個test cases來達到100%覆蓋率
1. B < C, today = Monday
2. B not equal to C, today = Wednesday


### Example 5

```
if Quantity >= 20
	Discount = 0.05
if Quantity >= 100
	Discount = 0.1
```

#### Statement test:
只要一個test case就達到100% Statement覆蓋率
1. Quantity = 105

## Decision Coverage

有些地方會稱為Branch Coverage
decision是在code裡面，為if, while, do while, 等等的數量
Test all decision outcomes in your code

DC = Decision outcomes covered / Total no. of decision outcomes

### Example 1
```
if x > 3
	print "hello"
```

#### Decision test
if會有兩種結果: yes or no
所以在這邊的coverage test要達到100%必須要有兩個測項
1. x = 5
2. x = 1

- 由此可知，有沒有可能只用1個test cases就可以達到100%的decision coverage?
  ans: 完 全 不 可 能!!
- Decision coverage 和 Statement coverage哪一個比較好?
  ans: Decision Coverage一定是比較好且較有效率，也是一種廣泛用在白箱測試的方式。而且100%的DC絕對也會是100%的SC。
  所以SC是DC的其中一個subset


### Example 2
```
if day == "Monday"
	then statement a
else
	statement b
end if
if day == Tuesday
	then statement c
end if
```

#### Decision test
if會有兩種結果: yes or no，所以這邊總共有4個decisions
所以在這邊的coverage test要達到100%必須要有兩個測項
1. day = Monday
2. day = Tuesday


### Example 3

```
Start
Do until B == C
	if today == Monday
		set A=1
	else if today == Wednesday
		set A=2, B=C
	end if;
	if B < C
		B = B + 1
	end if;
end loop
end
```

#### Decision test:
if和Do until會有兩種結果: yes or no，所以這邊總共有4個decisions

至少要有四個test cases來達到100%覆蓋率

|     | T   | B   | C   |
| --- | --- | --- | --- |
| TC1 | M   | 5   | 7   |
| TC2 | W   | 5   | 7   |
| TC3 | S   | 10  | 6   |
| TC4 | ?   | 6   | 6   |

## Condition Coverage

Test each condition in the code in true & false cases
測試code裡面所有的true和false條件

Decision 和 Condition的差異?

- if x > 3 這樣會有兩個outcomes
  這個同時為Decision和Condition
- if (x > 3) or (y > 5)
  這也是decision，我們只要測試有沒有過這行decision而已
  而如果是condition，我們會測所有的condition，這邊總共有兩個 x>3和y>5的true和false結果
- if (Grade>90) or (Student has a sportive achievement) or (Student has a disability)
  這會測3個condition

Condition Coverage測試了每一個conditon在true和false的狀態

### Example 1

```
read x
read y
if (x == 0) or (y > 0):
	y = y/x
else:
	x = y + 2
print(x)
print(y)
```

#### Condition test:

所以Condition coverage test要達到100%必須要有兩個測項
1. x = 5, y = 5
2. x = 5, y = -5


### Example 2
```
if number of books > 8 or sum > 100
	extra discount
```

#### Condition test:
這邊有兩個condition
所以Condition coverage test要達到100%必須要有兩個測項
1. number of books = 10, sum = 150
2. number of books = 5, sum = 50


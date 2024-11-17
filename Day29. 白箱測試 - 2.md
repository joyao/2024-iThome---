
## Path Coverage

測試code所有可能的路徑


### Example 1
```
if x > 3:
	print "Hi"
else:
	print "Bye"
if y = 5:
	print "Good"
else:
	print "Bad"
```

#### Path coverage
總共會有4個test cases => 每個path都要清到

### Example 2
```
input A & B
C = A + B
if C > 100:
	print "ITS DONE"

if A > 50:
	print "ITS PENDING"
END IF
```

#### Path coverage
總共會有4個test cases => 每個path都要清到
1. A = 60, B = 50
2. A = 20, B = 100
3. A = 60, B = 10
4. A = 20, B = 10

### Example 3

```
def foo(x, y):
	for i in range(x):
		something()
	if y:
		somethingElse()
```

#### Path coverage
以這種情形來說，沒有辦法去測試所有的Path，因為可能有無限個X的值，所以沒辦法達到100% Path coverage
這種情形又稱為 exhaustive testing，所以大多數的時候，Path coverage 100% 是沒有辦法達到的



## Modified Condition Decision Coverage (MCDC)

- 是condition Coverage和Decision Coverage的混合
- 在safety-critical application中是必要的
- IDEA: 只測試重要的condition的組合和limit testing cost
- 通常是用在有很多的condition的情形，並且不知道要測哪些才算有效的測試
- 以結果論來說4個條件我們會有5個test cases, 10個條件會有11個test cases而不是1024個

### Example 1

``` python
def x(a, b, c):
	if a & b & c:
		print("Hi")
```

#### MCDC Coverage

可能的測項

| Test Case | A   | B   | C   | Outcome |
| --------- | --- | --- | --- | ------- |
| 1         | T   | T   | T   | T       |
| 2         | T   | T   | F   | F       |
| 3         | T   | F   | T   | F       |
| 4         | T   | F   | F   | F       |
| 5         | F   | T   | T   | F       |
| 6         | F   | T   | F   | F       |
| 7         | F   | F   | T   | F       |
| 8         | F   | F   | F   | F       |

這時我們要找一個條件是會影響到outcome的
- TC1和TC5符合我們測試A的要求，並且BC不變
- TC1和TC3符合我們測試B的要求，並且AC不變
- TC1和TC2符合我們測試C的要求，並且AB不變

所以總結來說，我們只要測試以下測項就能達到100% MCDC Coverage

| Test Case | A   | B   | C   | Outcome |
| --------- | --- | --- | --- | ------- |
| 1         | T   | T   | T   | T       |
| 2         | T   | T   | F   | F       |
| 3         | T   | F   | T   | F       |
| 5         | F   | T   | T   | F       |


### Example 2

``` python
def x(a, b, c):
	if a | b & c:
		print("Hi")
```


#### MCDC Coverage

可能的測項

| Test Case | A   | B   | C   | Outcome |
| --------- | --- | --- | --- | ------- |
| 1         | T   | T   | T   | T       |
| 2         | T   | T   | F   | T       |
| 3         | T   | F   | T   | T       |
| 4         | T   | F   | F   | T       |
| 5         | F   | T   | T   | T       |
| 6         | F   | T   | F   | F       |
| 7         | F   | F   | T   | F       |
| 8         | F   | F   | F   | F       |
這時我們要找一個條件是會影響到outcome的
- TC2和TC6符合我們測試A的要求，並且BC不變
- TC5和TC7符合我們測試B的要求，並且AC不變
- TC5和TC6符合我們測試C的要求，並且AB不變


所以總結來說，我們只要測試以下測項就能達到100% MCDC Coverage

| Test Case | A   | B   | C   | Outcome |
| --------- | --- | --- | --- | ------- |
| 2         | T   | T   | F   | T       |
| 5         | F   | T   | T   | T       |
| 6         | F   | T   | F   | F       |
| 7         | F   | F   | T   | F       |

## Loop Testing

- 通常是用在當有loop在code裡面

### Example1

``` python
count = int(input("enter your number"))
while (couont < 20) & (count > 0):
	print(f"The count is: {count}")
	count = count + 1
print("Good bye!")
```

#### Loop Coverage

Steps:
1. Skip the entire loop: `count = 20`
2. Make 1 passes through the loop: `count = 19` 
3. Make 2 passes through the loop: `count = 18`
4. Make a random number of passes through the loop: `count = 10`
5. Make n, n-1, n+1 passed through the loop:
   `couont = 1`, `count = 0`, `count = 2`

### Example2

``` python
count_1 = int(input("enter first number"))
count_2 = int(input("enter second number"))
for i in range(count_1):
	for j in range(count_2):
		print(i, j)
		if i > 20 or j > 20:
			break
print("Good bye!")
```

#### Loop Coverage

Steps:
1. Skip the entire loop: `count_1 = 1, count_2 = 0`
2. Make 1 passes through the loop: `count_1 = 1, count_2 = 1`
3. Make 2 passes through the loop: `count_1 = 1, count_2 = 2`
4. Make a random number of passes through the loop: `count_1 = 1, count_2 = 5`
5. Make n, n-1, n+1 passed through the loop: 可以為無限值



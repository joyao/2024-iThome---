在進入測試領域之前，大部分的人應該都有一樣的疑問:
- 什麼是tc
- 要怎麼寫

- 有些只寫測試情境
- 有些只寫測試案例
- 有些兩個都寫


test scenario 或 test condition 只有一行敘述要測什麼而已，但tc包含了很多的欄位

## login form TC

### 1. Test Case Title

> Verify login with a valid username & password

這項跟test scernario或tes condition非常相似

### 2. Precondition

> User is already registered using valid credentials

這項非常重要，要先描述目前的狀態
ex. 要有網路連線、瀏覽器必須要更新 

有時候我們有一個Precondition給不只一個test case，有一群test cases，我們稱為 test suite

這個test suite包含一個precondition給所有的test case都在內 

### 3. Test steps

這個非常的重要，定義了測試的執行步驟順序 
但我們有時候並不需要test steps，照著test scenario就可以測試這個功能
但大多數的系統都很複雜

> 1. Enter a valid username
> 2. Enter a valid password
> 3. Click on sign in

至於開啟網站、註冊帳號、登入系統都不會寫在步驟內，因為這個算是precondition的範疇

### 4. Expected result

> User is logged in successfully and redirected to (XYZ) page

這項非常重要，因為這個結果是由各種考量與政策的結論


### 5. Test Scenario (Test Suite)

> Login

We always have a folder that includes test cases that are related to each other
實務上會用一個資料夾來整理test cases


### 6. Test Environment

> Windows 1 - Chrome - Wi-Fi Samsung
> Samsung Note 20 - Android 13 4G Network
> iPhone 15 Pro - iOS 16.2 - 5G Network

prd or non-prd

在哪些環境下測試

### 7. Actual Result

> Very important note: Never fill the actual result field until you execute the test case

非常重要，反映現實測試的成果
是pass還是不符合expect

### 8. Status

![[Pasted image 20240815011540.png]]


### Sample

![[Pasted image 20240815011823.png]]

![[Pasted image 20240815011838.png]]


## 撰寫第一支測項

建立一個Google sheet表格

### 註冊

#### Prerequisites
- The user has a valid phone number or email to sign up with

在 Scenarios 打勾表示已經寫成test case

#### Steps

1. Validate sign up with valid phone number
	1.1 Navigate to sign up page
	1.2 Provide a valid first name
	1.3 Provide a valid surname
	1.4 Provide a valid phone number
	1.5 Provide a valid password
	1.6 Provide a valid date of birth
	1.7 Provide a valid gender
	1.8 Click on "Sign up"

這是一個high level test case，因為我並沒有告訴他實際上要輸入什麼值
在某些情形下我們必須要寫Low level test case，像是EP, BVA

如果你的測試人員是個有經驗的人，最好是使用high level test cases 

也可以將上述步驟縮減

1. Validate sign up with valid phone number
	1.1 Navigate to sign up page
	1.2 Provide a valid phone number
	1.3 Fill all other fields with valid data
	1.4 Click on "Sign up"

取決於專案規範

#### Expected Result

- User registration is successful
- User is redirected to Newsfeed Page
- An OTP is sent to the user

#### Status
- Ready to Test
- Under Review
- Pass
- Fail
- Block / Skip

#### Priority
- High
- Low















 
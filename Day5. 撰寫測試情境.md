當需求已經被撰寫，你review後要去準備dynamic test

撰寫測試情形來去找到defects
A TEST SCENARIO is defined as any functionality that can be tested
又稱 test condition或test possibility

必須要把自己變成end user 並寫測項Application Under Test


## 如何撰寫test scenario

1. 謹慎的閱讀需求文件 BRS, STS, FRS, SUT
2. 分離出每個需求，並找出那些動作是需要被測試的。找出那些技術問題跟需求有關，並且記得要去分析和框出問題
3. 列舉測試情境來確保可以覆蓋到每個可能的software feature。包含 user flow和bussiness flow
4. 列舉完以後，建立可以追蹤的表格來確保每個需求都可以有對應的測項
5. 給supervisor review這些測項，並且reviewed by other stakeholder

## 搜尋一些常用的測試情境

### E-commerce Website
以下這些都是E-commerce website常見的測試案例
[https://blog.qatestlab.com/2023/04/10/cms-testing-ecommerce/](https://blog.qatestlab.com/2023/04/10/cms-testing-ecommerce/)
[https://testsigma.com/blog/test-cases-for-ecommerce-website/](https://testsigma.com/blog/test-cases-for-ecommerce-website/)
[https://www.qatouch.com/blog/how-to-write-test-cases-for-ecommerce-website-in-a-best-way/](https://www.qatouch.com/blog/how-to-write-test-cases-for-ecommerce-website-in-a-best-way/)

### 設定Trello

search for template: scrum board
可以用來建立test scenario -> add check list

### 開始建立Facebook註冊帳號的test cases

Facebook login and sign up

1. take sign up snapshot and add it in trello
2. 開始寫測試
3. 每一個欄位都有valid和invalid的值
4. 很長、亂碼、不符合規格
5. 從valid開始

#### Sign up page

##### Valid scenario:
1. Validate sign up with valid phone number
2. Validate sign up with valid email
3. Validate sign up with Chinese First and Surname
4. Validate sign up with Arabic First and Surname
5. Validate providing a short valid first or surname "E.g: jy hsu"
6. Validate providing a mobile number with and without country code "E.g. +8869123456789、09123456789、886916631438"
7. Validate sign with valid age in the range of 13 and 18 years old
8. Validate sign with valid age in the range of 18 and 120 years old
9. Validate providing different values for Gender


##### Invalid:
1. Validate leaving first name field empty
2. Validate leaving Surname field empty
3. Validate leaving email or phone number field empty
4. Validate leaving password field empty
5. Validate leaving gender field empty
6. Verify providing numbers or special characters in first name
7. Verify providing numbers or special characters in Sur name
8. Verify providing very short first name 'N'
9. Verify providing very short sur name 'N'
10. Verify providing very long first name 'more than 50 characters'
11. Verify providing a short mobile number "1234"
12. Verify providing a long mobile number "more than 15 digits"
13. Verify providing a space in the mobile number
14. Verify copy/paste mobile number from another website or application
15. Verify adding an email with wrong format (e.g. abc32423#)
16. Verify adding an email with a mistake in the format "xxxx@gamil.com"
17. Validate a password with less than 6 digits (e.g. A12#1)
18. Validate a password without letters (e.g. 12345!@#)
19. Validate a password without numbers (e.g. abcd!@#)
20. Validate a password without special characters (e.g. 123asdfw)
21. Validate providing a date of birth less than 13
22. Validate providing a date of birth more than 120

#### Snapshot password rules
1. Six digits
2. include numbers
3. includes letters
4. includes special characters

#### Login page

##### Login valid scenario:
1. Login with a valid email address and a valid password
2. Login with a valid phone number and a valid password
3. Login with different ways of writing phone number
4. Login with valid user without verifying email or phone number
5. Login with a valid password after using forgotten password functionality
6. Check show password button
7. Check copy/paste of password
8. Validate that after login user is redirection to Newsfeed page
9. Login with a deactivated account
10. Login with a suspended account

##### Redirections
1. Validate redirection to forgotten password
2. Validate redirection to Sign up page
3. Validate redirection to Create a page page

##### Login Invalid scenarios:
1. Login with leaving phone or email field empty
2. Login with leaving password field empty
3. Login with an invalid email "not registered"
4. Login with an invalid email "wrong format"
5. Login with invalid phone number "not register"
6. Login with invalid phone number "wrong format
7. Login with invalid password with valid email
8. Login with invalid password
9. Login with a valid password after being blocked form accessing the app
10. Login with providing an old password

### Compatibility Testing
1. Test using Chrome
2. Test using Firefox
3. Test using Edge
4. Test using Safari
5. Test using Safari on iPhone
6. Test using Chrome on iPhone
7. Test using Chrome on Android
8. Test using any browser on a tablet


### Conclusion




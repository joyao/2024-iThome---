
為什麼測試人員要學JIRA

1. Reporting defects
2. State testing (Remove activities)
   - SRS
   - BRD
   - Product backlog - INVEST
3. acceptance criteria
4. writing requirement & user stories -> act as a scrum master

jira -> software development
- Kanban
- Scrum
- Bug tracking - defect lifecycle
	- defects
	- tests

General: issue = defect = fault = bug
Jira: Issue includes epics, user stories, defects, tasks, subtasks


## Jira

project types:
- Team managed projects -> self-organized team
- Company managed projects -> jira admin
	- for big project


## Company managed project

select company managed project

![[Pasted image 20240821233123.png]]

Name - MyFirstProject
Key - MYF1

![[Pasted image 20240821233502.png]]


Project divided into components

### 1. Components
- Component #1 - Android-rider
- Component #2 - iOS-rider
- Component #3 - Android-driver
- Component #4 - iOS-driver
- Component #5 - iPad OS-rider
- Component #6 - Apple watch-rider
- Component #7 - iPad OS-driver
- Component #8 - Uber website
- Component #9 - Admin Panel

### 2. Epics

User rider
- Login
- Register
- Request a ride
- Leave a rating
- My previous trips
- My wallet
- Request a ride for a friend

Uber driver
- Login
- Register
- Accept a ride
- Decline a ride
- Leave a rating
- Balance
- Previous tips
- My rating
- My balance (withdraw)
- Set status (busy, active)


### 3. User Stories

Login
- As a user, I want to be able to login using phone number
- As a user, I want to be able to login using email address
- As a user, I want to be able to login using apple id
- As a user, I want to be able to save my login credential, so that I don't have to log in again each time I open the app


### 4. Tasks & subtasks

- Create wireframe for login -> @designers
- Develop login features -> @developer
- Create test cases for login functions -> @tester
- Perform case review for login functions -> @ developer
- Execute login test case & report feature defects -> @tester


## Add components

![[Pasted image 20240821235114.png]]

Backlog空白是正常的，因為它只顯示issue

## Create Epics

![[Pasted image 20240821235529.png]]


勾選 Create another issue

建立列表
但backlog還是看不到很正常，因為backlog本身有時效性等
如果打開Epic panel會看得見

![[Pasted image 20240822000535.png]]



## Create Versions/Releases


### Release / Version
- Shipped to users or clients
- ready for deveployment
- QA -> Client


### Build
- Executable file (.apk)
- Still under testing
- Dev -> QA

![[Pasted image 20240822001301.png]]


## Create User Stories

![[Pasted image 20240822001924.png]]

![[Pasted image 20240822002755.png]]


## Create acceptance Criteria

- 確認user stories are done
- DoD = Definition of Done
- 每一個User story 都要有DoD
	- written
	- reviewed (INVEST)
	- All tasks are written
	- All acceptance criteria are specified
	- All acceptance criteria should be implemented or tested

 >As a user, I should be able to login  using phone number
 
Acceptance Criteria

Check list based
 1. A place holder appears in Phone number field
 2. User can change country code from the list of countries
 3. OTP button is disabled as long as user didn't enter a valid phone number
 4. Phone number field should only accept numeric values
 5. User can only enter valid number of digits in Phone number field which is relevant to the country that he logs in from.

Scenario based
- BDD (Behavior-driven development) Churkin format
- `Given`  some initial state
	- Given that user enter a valid phone number
- `When` user does some action
	- When user clicks/taps on "send OTP" button
- `Then` system response with specific actions
	- Then an OTP is sent to the user and he can user it to login to the app

- `Given` user entered a valid phone number
- AND user entered an invalid OTP
- When user tries to validate his OTP
- Then the system shows an error message telling user that OTP is wrong and asks him to enter it again


As a user, I want to be able to recover my password so that I can access my account in case I forget the password.
- GIVEN user navigate to login page
- WHEN user clicks on "forget password" password and enter a valid email to receive link
- THEN system sends the link to the entered email


Write acceptance criteria in user story's description field

![[Pasted image 20240822212315.png]]

![[Pasted image 20240822212838.png]]

![[Pasted image 20240822212755.png]]

![[Pasted image 20240822212817.png]]


Create a bug

![[Pasted image 20240822214337.png]]



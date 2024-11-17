
1. 會在Postman建立一個Project
2. 而這個API Testing Project是用來測試Trello board creation的

- Create Board
- Create a list inside this board
- 在每個List中建立Card
- 新增Checklist 等資訊在card 內

自動化建立這些

## Trello API

https://developer.atlassian.com/cloud/trello/rest/api-group-actions/

![[Pasted image 20240826222814.png]]

## Create Board in Trello APIs

![[Pasted image 20240826222933.png]]


Type: POST
URL: https://api.trello.com/1/boards/
Params:
- name = Bootcamp_test
- key = `<your api key>`
- token = `<your token>`

https://developer.atlassian.com/cloud/trello/guides/power-ups/managing-power-ups/#adding-a-new-custom-power-up

Key 和 token可以從以下網站取得
https://trello.com/power-ups/admin

![[Pasted image 20240826224100.png]]

New
![[Pasted image 20240826224359.png]]

Create
![[Pasted image 20240826224417.png]]

Generate a new API key

只有14天的有效期
![[Pasted image 20240826224455.png]]

## Generate Token

![[Pasted image 20240826224949.png]]


- set  https://api.trello.com/ as base.url


![[Pasted image 20240826225031.png]]

![[Pasted image 20240826225132.png]]


### Delete Board

URL: https://api.trello.com/1/boards/<id>

![[Pasted image 20240826230111.png]]


### Set key an token as variable

![[Pasted image 20240826230701.png]]



## 建立測試排程

### 寫test cases

| Category  | Requests         | Dependency                         | Priority |
| --------- | ---------------- | ---------------------------------- | -------- |
| Board     | Create board     | None                               | Critical |
|           | Update board     | Create board                       | Hight    |
|           | Read board       | Create board                       | Medium   |
|           | Delete board     | Create board, Update board         | Low      |
| List      | Create list      | Create board                       | Critical |
|           | Update list      | Create list                        | Hight    |
|           | Get list         | Create list                        | Medium   |
|           | Delete list      | Create list, Update list           | Low      |
| Card      | Create card      | Create list                        | Critical |
|           | Update card      | Create card                        | Hight    |
|           | Get card         | Create card                        | Medium   |
|           | Delete card      | Create card , Update card          | Low      |
| Checklist | Create checklist | Create card                        | Low      |
|           | Update checklist | Create checklist                   | Low      |
|           | Get checklist    | Create checklist                   | Low      |
|           | Delete checklist | Create checklist, Update checklist | Low      |

### Test Execution Schedule

| Order |                  |
| ----- | ---------------- |
| 1     | Create board     |
| 2     | Create list      |
| 3     | Create card      |
| 4     | Update board     |
| 5     | Update list      |
| 6     | Update ard       |
| 7     | Read board       |
| 8     | Read list        |
| 9     | Read card        |
| 10    | Create checklist |
| 11    | Update checklist |
| 12    | Get checklist    |
| 13    | Delete checklist |
| 14    | Delete card      |
| 15    | Delete list      |
| 16    | Delete board     |


![[Pasted image 20240826233058.png]]


Delete change to use board_id variable
![[Pasted image 20240826233503.png]]

Run collection
![[Pasted image 20240826233640.png]]

![[Pasted image 20240826233725.png]]

## 新增測項


Create
``` js
var jsonData = pm.response.json()

// pm.globals.set("variable_key", "variable_value")

pm.globals.set("board_id", jsonData.id)

pm.test("Board created successfully", function() {
    pm.response.to.have.status(200)
} )

pm.test("Reasonable response time", function (){
    pm.expect(pm.response.responseTime).to.be.below(3000)
})

pm.test("Correct board name", function() {
    var jsonData = pm.response.json()
    pm.expect(jsonData.name).to.eql("Bootcamp_test1")
})
```

Delete
```js
pm.test("Board deleted successfully", function() {
    pm.response.to.have.status(200)
} )

pm.test("Reasonable response time", function (){
    pm.expect(pm.response.responseTime).to.be.below(3000)
})
```

![[Pasted image 20240826234518.png]]

### Common test cases

直接點選資料夾 -> Scripts -> Post-response

![[Pasted image 20240826234709.png]]


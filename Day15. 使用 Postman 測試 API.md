
## 什麼是Postman

- Postman是一個軟體可以用來測試你的REST API或是外部提供的API
- Postman是一個瀏覽器

可以從Postman的官網下載並安裝
https://www.postman.com/

### Get request

![[Pasted image 20240823165430.png]]

status code 200

Preview
![[Pasted image 20240823165555.png]]

設定參數
![[Pasted image 20240823165905.png]]

### Post Request

![[Pasted image 20240823170225.png]]

### Writing Tests

Post-response
``` js
pm.test("Status code is 200", function(){

    pm.response.to.have.status(200);

})
```

![[Pasted image 20240823170502.png]]

![[Pasted image 20240823170546.png]]

![[Pasted image 20240823171323.png]]

批次run collection
![[Pasted image 20240823171654.png]]


### 測試範例網站

https://reqres.in/
![[Pasted image 20240823172138.png]]

![[Pasted image 20240823172343.png]]

tests
![[Pasted image 20240823173046.png]]

## Create & Use environment

![[Pasted image 20240823173611.png]]

![[Pasted image 20240823173753.png]]


### Authorization and Authentication

不同的API或user會有不同的權限

所謂的認證(authentication)，我們就想像為通行證的概念，就以企業來說，我們每個人進到公司都會收到一張員工通行證，而這張員工通行證也註冊了屬於你這個人的唯一識別資訊，當我們上班前刷卡這個動作其實就是一個認證(authentication)的過程，讀卡機讀取我們的卡片資訊，送到伺服器系統進行比對之後，確定這個人是該公司的員工才能開門進入公司上班。

而授權(authorization)則是經過認證(authentication)之後被賦予的權力，以上述例子來說，當我們進到企業工作時，通常根據應徵職位被賦予工作上的權力，例如： 財務長被授予管理公司財務的權責、IT被賦予管理硬體的權責…，每個人根據職位扮演的角色，被賦予對應的權責，相同的授權方式，常見的論壇(一般用戶、管理員)、大樓門禁(保全、住戶)…等，都隱含著認證與授權的概念。

https://vocus.cc/article/644c77edfd897800015881c4

![[Pasted image 20240823174716.png]]


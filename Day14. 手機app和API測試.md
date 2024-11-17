
## Mobile Testing

測試流程和文件那些在任何一個application都一樣

### 不同類型的mobile application
- web
- hybrid
- native

#### Native Mobile Application
- 原生的application
- 效能較好
- 費用較高 (Android, iOS)
- 直接安裝在手機上
- ex. Google maps, Facebook, LinkedIn

測項在Android上pass的不一定可以在iOS上passed，他們是不同的application，應該要分成兩個不同的Projects

#### Browser-based Application
- 從手機的瀏覽器開啟
- 花費較少
- 開發較簡單
- Browser Compatibility testing is required
	- ex. Edge, Chrome, Firefox,...

要有網路才可以連上系統

#### Hybrid Mobile Application
- 原生和web的結合
- 網頁包在app內
- 開發較簡單
- 可以離線操作

效能介在中間



### 不同的mobile device

#### Basic Phones
- 只有通話和SMS
- 只有提供幾個內建的APP和遊戲
- 安裝APP和瀏覽網頁是不可能的

#### Feature Phones
- 只有一些少數支援的app
- 可以用內建的瀏覽器上網
- 可能會有一些額外的硬體，像是相機

#### Smartphones
- 有很多不同的感測器
- 可以安裝app

#### Tablets
- 跟smartphone很相似
- 但可以支援較長的電池
- 並非每個平板都支援sim卡和打電話 (OTP不支援)

#### Wearables
- 通常跟智慧手機或平板一起使用
- 提供一些特殊app的支援


### 挑戰
- 不同的平台和設備
- 不同的UI設計和UX期望
- 不同的網路類型
- 舊機型的支援
- 不同的使用者
- 高度可見的意見回饋
- Marketplace (app store) 的同意發布權限
- 新設備可能無法使用


### Mobile Analytics Data

- 哪個裝置是在哪個國家最熱門的

可以從這個網站上看到
https://gs.statcounter.com/


World wild

![[Pasted image 20240822224014.png]]

In Taiwan
![[Pasted image 20240822224109.png]]

OS

![[Pasted image 20240822224317.png]]

Android Version
![[Pasted image 20240822224433.png]]


可以從中選擇優先測試的版本，套用80/20法則
測試20%的測項可以涵蓋80%的功能



## API Testing

API是寫網頁最基本的基礎知識：怎麼去call API?

SATE OF TESTING REPORT

API = Application Programming Interface

3個部分用於資料的傳輸
- Request
- Program
- Response

通常使用xml或json來當作資料格式
也使用soap, rest, xml/rpc進行資料的傳輸

> 跳過API的介紹

XML格式範例

``` xml
<InvitationList>
	<family>
		<aunt>
	    <name>Christine</name>
	    <name>Stephanie</name>
	    </aunt>
	</family>
</InvitationList>
```

JSON格式範例

```json
{
	"InvitationList": {
		"family": {
			"aunt": {
				"name": [
					"Christine",
					"Stephanie"
				]
			}
		}
	}
}
```


SOAP APIs
- SOAP = Simple Object Access Protocol
- 使用 WSDL
- 使用XML傳輸格式


REST APIs
- Stateless
- 使用JSON格式
- GET, POST, PUT, PATCH, DELETE

明天會使用POSTMAN來測試API，這些都已經有在上一個系列的 web 開發展示過了


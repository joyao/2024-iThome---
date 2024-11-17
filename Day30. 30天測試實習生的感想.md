
在經歷過30天學習測試後，對測試的工作內容已經有基本的了解了。
身為開發人員，一直以為的測試都是寫寫code或是用selenium去跑ui測試，用自己的想法去想說要測哪些項目、要輸入哪些值，只要有測到就算測過。
但在經過這30天我學到了怎麼寫test scenario, test cases, user story 和怎麼去開defect report，也才知道原來公司的那些系統和validation team所說的那些名詞和文件原來是這樣來的，測試遠比我想像的還要複雜。

一直以來軟體界都有個大家不願承認的鄙視鏈: 軟體工程師 > 軟韌工程師 > web工程師 > 其他工程師 >>> 測試工程師
就連本身身為軟體 + 韌體 + web 工程師的我，在被assign到要去寫測試的時候，都會時不時聽到同事們覺得測試很簡單、測試不重要的這些細碎言論，也理所當然地不想要用這套系統，但自己開發測試又不確實，導致release的時候抓到一堆defect。
如果我們可以落實自動化測試、regression 測試，是不是可以將測試左移，提前發現問題提早解決。但如果工程師們都覺得不重要、不想改變，這套也推不下去，終究只是個口上說說的理想框架。

## 測試真的這麼簡單嗎?

我不知道為什麼要有上述說的鄙視鏈，如果有人真的覺得測試這麼簡單，那我一律建議自己下來做做看就知道了。

身為工程師在學這些之前，我心裡有一些疑問：
1. 測試就是找一些功能下去測，最好是達到100%的覆蓋率，但我知道不可能，所以也不會評估怎麼算覆蓋率
2. 測試到底是要開發人員去做還是測試人員去做?
3. 在有限的時間內，要怎麼去評估某項功能該不該做測試? 該做多少測試?
4. 在開發feature的時候會看到validation team會寫test cases，裡面有步驟，但我隨便寫就可以了嗎?
5. 拿到defect ticket的時候，裡面要有哪一些內容才是正確且有效溝通的report? 如果今天是我要發defect，要注意哪些內容?
6. 要怎麼去算測試覆蓋率?

我想要學測試的其中一個目的：了解它的內容和技巧、不要讓自己跟其他人一樣在不了解的情況下就預設它很簡單。

但缺點是在深入了解測試以後，會更對那些鄙視測試的人不爽；或是有些自己明明就做測試的人，連最基本的觀念都沒有，有時候是真的會有點無奈。

## 30天回顧

- [Day1. 30天入門測試](https://ithelp.ithome.com.tw/articles/10349649)
- [Day2. 專案成員角色與SDLC](https://ithelp.ithome.com.tw/articles/10349660)
- [Day3. 基本的測試觀念 - 1](https://ithelp.ithome.com.tw/articles/10350042)
- [Day4. 基本的測試觀念 - 2](https://ithelp.ithome.com.tw/articles/10350174)
- [Day5. 撰寫測試情境](https://ithelp.ithome.com.tw/articles/10350179)
- [Day6. 黑箱測試](https://ithelp.ithome.com.tw/articles/10350199)
- [Day7. 如何撰寫test case](https://ithelp.ithome.com.tw/articles/10350210)
- [Day8. 使用Zephyr Scale來撰寫test cases](https://ithelp.ithome.com.tw/articles/10350213)
- [Day9. 執行測試、回報Bugs與測試報告](https://ithelp.ithome.com.tw/articles/10350220)
- [Day10. 測試工程師面試十題題解](https://ithelp.ithome.com.tw/articles/10350224)
- [Day11. Agile Project的管理 - 1](https://ithelp.ithome.com.tw/articles/10350227)
- [Day12. Agile Project的管理 - 2](https://ithelp.ithome.com.tw/articles/10350233)
- [Day13. 如何使用JIRA進行 Agile testing](https://ithelp.ithome.com.tw/articles/10350237)
- [Day14. 手機app和API測試](https://ithelp.ithome.com.tw/articles/10350241)
- [Day15. 使用 Postman 測試 API](https://ithelp.ithome.com.tw/articles/10350244)
- [Day16. API 測試 - 以Trello API為例](https://ithelp.ithome.com.tw/articles/10350248)
- [Day17. Performance Testing - 1](https://ithelp.ithome.com.tw/articles/10350251)
- [Day18. Performance Testing - 2](https://ithelp.ithome.com.tw/articles/10350253)
- [Day19. 進階 Performance Testing](https://ithelp.ithome.com.tw/articles/10350256)
- [Day20. Selenium IDE](https://ithelp.ithome.com.tw/articles/10350258)
- [Day21. 利用Katalon Studio進行自動化測試](https://ithelp.ithome.com.tw/articles/10350600)
- [Day22. 兼職測試工程師接案網站](https://ithelp.ithome.com.tw/articles/10350631)
- [Day23. 用Playwright來進行自動化測試 - 1](https://ithelp.ithome.com.tw/articles/10350634)
- [Day24. 用Playwright來進行自動化測試 - 2](https://ithelp.ithome.com.tw/articles/10350641)
- [Day25. 用Playwright來進行自動化測試 - 3](https://ithelp.ithome.com.tw/articles/10350643)
- [Day26. 用Playwright來進行自動化測試 - 4](https://ithelp.ithome.com.tw/articles/10350650)
- [Day27. 用Playwright來進行自動化測試 - 5](https://ithelp.ithome.com.tw/articles/10350653)
- [Day28. 白箱測試 - 1](https://ithelp.ithome.com.tw/articles/10350660)
- [Day29. 白箱測試 - 2](https://ithelp.ithome.com.tw/articles/10350666)
- [Day30. 30天測試實習生的感想](https://ithelp.ithome.com.tw/articles/10350668)

## 後續加強部分

這30天主要都學到的是軟體測試，後續我想要加強以下幾點:
- 韌體測試
- 要怎麼用數據的方式去評估該不該寫自動化測試，畢竟寫測試的script也是需要花時間
- 如何使用robot framework

到此感謝大家看完我30天的自我挑戰筆記，願大家都能尊重每一項專業的技術。


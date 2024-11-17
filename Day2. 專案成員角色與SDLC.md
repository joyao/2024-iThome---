

## 專案成員

- Requirement Engineer
- UI/UX Designer
- Front-end, Back-end, Mobile Developers
- Project Manager & Scrum Master
- QA


## SDLC

### What is SDLC

https://aws.amazon.com/tw/what-is/sdlc/
>軟體開發生命週期 (SDLC) 是經濟實惠且節省時間的程序，開發團隊會用來設計並建置高品質的軟體。SDLC 的目標是透過事先規劃將專案風險降至最低，這樣軟體即可在生產期間和日後滿足客戶的期望。此方法概述一系列步驟，將軟體開發程序劃分為您可以指派、完成和衡量的任務。

可以分為 Waterfall 瀑布式開發, V-model 開發 還有 Scrum , Agile 敏捷式開發
~~有些公司可能還有隕石式開發~~

![[Pasted image 20240912003649.png]]

https://reliasoftware.com/blog/v-model
### Waterfall Model
- 該模型將系統發展的過程，大致區分為四個階段：分析、設計、實作、測試，其並且明確的定義每一階段中的工作
- 當完成一個階段的工作以後，才會進入下一個階段的工作。而依照該模型的系統發展的過程，即如同瀑布一般。
- 經過改良的瀑布模型，在發現上一個階段的工作不夠完善時，尚可以回溯至上一個階段中。
- 使用這種模型的開發方式常常會需要耗時很久才會到測試階段，會導致錯誤無法及時的被發現和修正。

### V-Model
- 是一種延伸自瀑布模型的軟體開發過程，是通用V模型的一個例子。
- V模型的軟體開發不是以直線的方式進行，其過程在原始碼階段之前逐步往下，而在原始碼階段之後逐步往上，形成了V字形。
- V模型指出了軟體開發中的各階段以及其對應軟體測試階段之間的關係。橫軸表示時間或是專案的完成度，而縱軸表示抽象的程度（範圍越大，越抽象的在越上方）。
- V模型主要的重點是要表示每一個步驟都跟測試有相關，不管事測試的規劃、寫測試案例還是實際得下去測。

### Scrum , Agile 敏捷式開發
https://kaichenlab.medium.com/%E6%B7%B1%E5%85%A5%E6%B7%BA%E5%87%BA-%E6%95%8F%E6%8D%B7%E8%BB%9F%E9%AB%94%E9%96%8B%E7%99%BC-scrum-%E4%B8%8B-acba23f3dca1

- 是一種應對快速變化需求的軟體開發模式，描述了一套軟體開發的價值和原則。
- 自組織的跨功能團隊在緊密的協作中發掘使用者或顧客的需求以及改良解決方案
- 此模式也強調適度的計畫、進化開發、提前交付與持續改進，並且鼓勵快速與靈活的面對開發與變更。
- 使方式可以更快的提交成果給客戶，即時的去修正所要展示的成果。

![[Pasted image 20240912004151.png]]

### ~~隕石式開發法~~
純屬好玩和梗，卻讓人無比的感受似曾相似的感覺，提供大家參考

日文版：[https://eiki.hatenablog.jp/entry/meteo_fall#google_vignette](https://eiki.hatenablog.jp/entry/meteo_fall#google_vignette)
中文版：[https://www.ptt.cc/bbs/Soft_Job/M.1527761485.A.1B2.html](https://www.ptt.cc/bbs/Soft_Job/M.1527761485.A.1B2.html)

神說要有光就有了光
![[Pasted image 20240913001203.png]]

---


## 商業需求規劃書 Business Requirement Document (BRD)
https://www.pmtone.com/business-requirement-document/
- 是「一份企業想要運用產品或服務實現目標的藍圖。」
- 則涵蓋新產品開發專案所有的可交付成果（如：市占率可提升10%）以及與每個階段相關的輸入（inputs）和輸出（deliverables）。
- 目的是讓決策者們從制高點的角度去了解：
	- 為何要做這個產品？
	- 需要多少資源（如：人、設備、時間、錢）？
	- 可以幫公司帶來哪些效益？
	- 可以提升哪些競爭優勢？
	- 商業模式是什麼？


## 軟體需求說明書 Software Requirement Specification (SRS)

- 軟體需求說明是軟體系統需求的規格化說明，是對將要開發系統的行為的說明。
- 軟體需求說明是在商業需求規格（或稱為利益相關者需求規格，StRS）產生後再建立的模型。
- 它包括功能性需求及非功能性需求，非功能性需求對設計和實現提出了限制，比如性能要求，質量標準，或者設計限制，也可能會包括用例，敘述在理想情形下，使用者使用軟體的方以及需要提供給的介面。
- 軟體需求說明是客戶和供應商（或承包商）協議的基礎，說明軟體產品應該有的機能（若是由行銷所驅動的專案，會是行銷部門以及開發部門進行這些討論）。



The BRD cares about the client himself or the end customer. The SRS cares about the development team.


![[Pasted image 20240810115525.png]]

https://www.geeksforgeeks.org/difference-between-brd-and-srs/
---
title: 一文看懂 API、Restful 與 Restful API 
date: 2024-04-17 11:55:50
tags:
    - api
    - http
---

大型語言模型（LLM）、GenAI 和 ChatGPT 等熱門技術詞彙已經成為我們日常對話中的常客，幾乎人人都在間接或直接的使用它們。為什麼？ 企業發布了 「API」 後，我們又能站在巨人的肩膀上，開發更強大的產品和服務...

<!-- more -->

![OpenAI 提供如何使用 API 的 Document](https://i.imgur.com/x5z9JtB.png)

### API

**是什麼？** 

API（Application Programming Interface，應用程式介面），簡單理解就是，我們不需要知道它實際如何運作，只要知道怎麼使用它。 就算不懂模型如何製作出來的，我更在意這個模型可以幫助我們在產品上的加值。因此會更在意：「輸入的方法」以及「輸出的結果」。


**如何運作？**

還是要簡單理解一下 HTTP，全名 Hypertext Transfer Protocol（超文本傳輸協定），是一種傳輸協定，需要用一定規格的語言來溝通。HTTP 就是用戶端和伺服器端之間的傳輸協定，如果用生活例子來理解會更好懂：

「去手搖店點一杯飲料」，步驟是這樣：

- 使用者打開瀏覽器，輸入網址按下 enter （我跟店員點了珍珠奶茶）

- 伺服器收到瀏覽器的 request，檢查該網址是否存在（店員先確定珍珠奶茶還沒賣完）

- 伺服器發送 response 給客戶端（店員把珍珠奶茶做好之後，拿給我）

以上可能有其他存在情境，對吧？ 例如，賣完了、需要無糖去冰、更改或取消等，這些規範包含：

- Method：包括 GET（獲取）、POST（提交）、PUT（更新）、DELETE（刪除），告訴伺服器對資源執行的具體操作。就像你在手搖店，你可能要點品項、取消品項或更改品項等。

- Status code：告訴客戶端請求是成功還是失敗，以及具體的失敗原因。常見的狀態碼包括 200（成功）、404（未找到）、500（伺服器錯誤）。這如同店員告訴你「珍珠奶茶準備好了」或「珍珠奶茶賣完了」。

- Headers：HTTP request 和 response 也包含例如內容類型 (Content-Type)，描述了傳送數據的格式（如 application/json）

- Stateless：HTTP 是一個無狀態的協議，是指每個請求之間是獨立的，伺服器不會記住之前的請求。就像每次去飲料店，員工還是要問你要喝什麼。如果需要持續追蹤顧客的偏好，飲料店需要額外的記錄系統；同理，網站會使用 cookies 或 session 來「記住」用戶的設定或登入狀態。

<hr>

### Restful & Restful API
 
REST，全名 Representational State Transfer (表現層狀態轉移)，它是一種「設計風格」，因此，以此規範設計的 API，稱為 RESTful API，又為遵循著 REST 架構風格的 API。

描述了如何實現 Web API 的架構，基於 HTTP 協定，用來建立分散式系統，並支援多種程式語言，他的優點包含：

- 可擴展性：系統無需保留 Client 狀態，因此可以提高擴展效能。就像連鎖快餐店不需要記住每位客人的喜好，也能應對客流增加。

- 靈活性：由於 Client 與 Server 完全分離，代表開發團隊可以只更新網站的前端或後端。

- 獨立性：開發者可以使用不同的程式語來寫，而不會影響API的整體設計。就像使用樂高積木搭建，可以選擇不同顏色和形狀的積木。

![發出 Request 包含 URL endpoint 和 HTTP verb 以及回傳 JSON 格式](https://i.imgur.com/sJb3TlS.png)

1. URL endpoint : 這是一個網址連結，代表我們想訪問的資源。

2. HTTP verb : 對 URL endpoint 的資源進行何種操作。

3. Status codes : 伺服器接收 RESTful HTTP 請求後，除請求資源外，會回傳 HTTP 狀態碼。

舉例來說，如果你在使用一個購物網站的 API 來查詢產品，一個 Restful 的 API 可能會這樣設計：

| HTTP verb   | URL endpoint | 描述             |
|-----------|----------------|------------------|
| GET       | /products        | 獲取所有商品列表   |
| GET       | /products/{id}   | 獲取特定商品資訊   |
| POST      | /products        | 新增商品         |
| PUT       | /products/{id}   | 更新特定商品資訊   |
| DELETE    | /products/{id}   | 刪除特定商品    |

<hr>

### 你知道 Postman 嗎？

[Postman](https://www.postman.com/product/what-is-postman/) 是開發與測試 API 的必備工具！無論是進行基本的 CRUD API 測試，還是需要包含 Header 資訊的複雜請求（比如帶 token 的身份驗證），當然也可以測試上傳/下載檔案 API。

References:
https://www.explainthis.io/zh-hant/swe/restful-api
https://mannhowie.com/rest-api
https://www.postman.com/what-is-an-api/#benefits-of-apis
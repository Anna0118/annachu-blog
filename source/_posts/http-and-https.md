---
title: Http 和 Https：差一個「s」這麼重要？
date: 2024-04-03 11:10:30
tags:
    - http
---

朋友寫了一封派對邀請函，周六下午在他家舉辦派對（HTTP）。但是信件被一位鄰居攔截且竄改了時間...

<!-- more -->
<img src="https://i.imgur.com/21yhcHI.png" width="70%" height="30%">

### 🔹HTTP

`HTTP` 全名 超文本傳輸協定（HyperText Transfer Protocol），內容規範了客戶端請求與伺服器回應的標準。 定義了多種類型的請求和回應。例如，如果你想要從一個網站檢視一些資料，您會傳送 HTTP GET 請求。如果您想要傳送一些資訊，例如填寫聯絡表單，則會傳送 HTTP POST 請求

同樣，伺服器以數字代碼和資料的形式，傳送不同類型的 HTTP 回應。以下是一些範例：

- 200 - 確定
- 400 - 錯誤請求
- 404 - 找不到資源

Web 端與 Server 端進行通訊是使用"明文"的方式，因為 HTTP 協議本身並不具備加密的功能，所以無法對請求端以及回應端的內容進行加密。就像標題的例子，當鄰居攔截這封信並竄改時間後，最終送達手中的信也無法辨識其真偽。

為了防止信息被竄改的風險，可以用一種特殊的信封，就是 `HTTPS`。這種信封配備了專用的鎖，只有發送者和接收者持有匹配的鑰匙，因此即便信件在途中被人攔截，沒有鑰匙的人也無法打開它，從而保障了信件的安全性。

### 🔹HTTPs

![Google 的網址使用的是 HTTPS 協定](https://r2.easyimg.io/g87oyfk6m/google_https.png)


`HTTPS` 全名 超文本傳輸安全協定，那個 S 就是 Secure 的意思；HTTPS 透過 HTTP 進行通訊，但通訊過程使用 SSL/TLS 進行加密，在 HTTP 之上定義了相對安全的資料傳輸方法。

HTTPS 網站需向獨立的憑證認證機構（CA）申請 SSL/TLS 憑證。在網站與瀏覽器交換資料前，會先共享這份憑證來建立信任關係。SSL 憑證中含有加密信息，確保資料交換的安全。

👍 HTTPs 對網站有好處：
- 強網路安全，防止資料被竊聽或篡改
- 提升 SEO 排名，幫助網站在 Google 搜索結果中獲得更好位置
- 增加用戶信任，透過瀏覽器安全鎖圖示讓用戶感到信息交換的安全性

<hr>

#### Take-Home Messages

- 透過申請 SSL/TLS 憑證，網站能夠實現 HTTPS 加密通訊
- 使用 HTTPS 協定的網站可以保障數據在傳輸過程中的安全性，防止數據被竊聽或篡改




參考資料 : [HTTP 與 HTTPS 之間有什麼區別？](https://aws.amazon.com/tw/compare/the-difference-between-https-and-http/)

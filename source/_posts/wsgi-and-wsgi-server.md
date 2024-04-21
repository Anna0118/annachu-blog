---
title: Flask 開發完後，進入部署？還得解鎖 WSGI 與 Nginx
date: 2024-04-02 17:37:30
tags: 
    - flask
categories: Deploy
---

使用**Python Flask** 框架寫了一個網站，然後現在需要**部署**到伺服器，得要知道WSGI...

<!-- more -->

![Serve Flask application with Gunicorn Nginx on ubuntu](https://i.imgur.com/jKI0eSF.png)

### 什麼是 WSGI?

WSGI 全名是 Web Server Gateway Interface，是制訂網站伺服器 (Web server) 與應用程式伺服器 (Application server) 之間的標準溝通協議，規範了 HTTP Request 如何與 Application Server 溝通。

<font size=2.5px color=#808080> 補充：[PEP 333](https://peps.python.org/pep-0333/) 是 Python 的一個提案，提出 WSGI 的規範，促使 Python 在 Web 開發領域的應用和發展。</font>

> 補充：
>
> #### Web Server vs. Web Application
>
> - Web Server : 負責處理 HTTP 協定的傳輸以及接受 HTTP request 與回傳 HTTP response。專注於傳送靜態資料。
> - Application Server : 負責管理並執行業務邏輯以及資料庫的存取。不直接與客戶端透過 HTTP 協定溝通，而是處理從 Web Server 傳過來的請求，並將執行結果回傳。
>
> 可以將 Web Server 看作是一種「中間人」角色！它接收來自客戶端的請求，轉發給 Application Server 執行相關程式，之後再將結果通過 HTTP 協定回傳給客戶端。


<hr>

###  WSGI 和 WSGI server有不一樣嗎？

WSGI 跟 WSGI server 這兩個名詞常常會搞混：
- WSGI 是協議規範。
- WSGI server 是遵照 WSGI 規範的 server，像是 [Gunicorn](https://gunicorn.org/), uWSGI。

![Gunicorn的官網介紹說明是 Python WSGI server](https://r2.easyimg.io/bh8mgaun3/截圖_2024-04-02_下午6.36.23.png)

> 補充：
> ####  WSGI vs. ASGI 
> - ASGI 全名是 Asynchronous Server Gateway Interface，WSGI 與 ASGI 都是個中繼站 (Middleware) 角色。
> - ASGI 的出現則是為了解決 Python 中常用的 WSGI 在當代Web開發中的局限性。例如，WSGI不支持新興的Web協議，例如 WebSocket。而ASGI 支持異步處理，因此適合於實現即時通訊。

<hr>

### 為什麼需要 Guicorn ?

當我們使用 Flask 或 Django 這樣的 Web 框架開發應用時，通常會借助於框架提供的簡易伺服器來快速啟動和運行開發環境。但這些內建的伺服器不適合用於生產環境 (Production)。
> 使用 Flask 框架內建的伺服器時，常常會看到一個警告，提醒我們它主要是為了開發目的而設計的。

![使用 Flask 框架內建的伺服器，可以看到Ｗarning](https://r2.easyimg.io/fyrunws04/development_server.png)

因為內建的伺服器缺乏處理大量連線的能力。這時 `Gunicorn` 就扮演了重要的角色，作為一個遵循 `WSGI` 協議的伺服器，不僅提供了更強大的性能和靈活性，還能夠確保應用在生產環境下的穩定運行。
<hr>

###  為什麼又需要 Nginx ?

[Nginx](https://www.nginx.com/) 是一款開源的網路伺服器，能夠用於多種網路服務，包括 HTTP 伺服器、反向代理伺服器、郵件代理伺服器等。常見的 Web server 軟體有 `Apache`、`Ngin` 等。

Nginx 可以提高網站效能和處理請求的能力：

- 靜態檔案快取：幫助“存放”網站上經常使用的資料（比如圖片、CSS 樣式表和 JavaScript 檔案），讓使用者訪問網站時能快速獲得這些資料，減少了等待時間和網絡流量消耗。
- 負載平衡：想象一個超市開設了多個收銀台來應對高峰期的客流量，Nginx 確保每個伺服器都能在承受能力範圍內工作，可以加速響應時間，提高用戶體驗。
- 反向代理：扮演中間人角色，幫助處理和分配來自外部的請求到內部的一個或多個伺服器，增加了額外的安全層，因為外部請求並不直接與內部系統互動。

<hr>

### Take-Home Messages

- Application Server: `Flask`, `Django` 
負責商業邏輯處理、根據URL、參數不同，執行不同的程式碼
- WSGI Server: `gunicorn`, `uWsgi`
根據WSGI協定，負責溝通，將 Web 請求轉換成應用程式能理解和處理的格式
- Web Server: `Nginx`, `Apache`
靜態檔案快取、負載平衡、反向代理

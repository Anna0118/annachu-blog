---
title: 為什麼我們知道WSGI?
date: 2024-04-02 17:37:30
tags: 
    - Python
    - Deploy
---

使用**Python Flask** 框架寫了一個網站，然後現在需要**部署**到伺服器，得要知道WSGI...

<!-- more -->

#### 🔹 什麼是 WSGI?

WSGI，全稱 Web Server Gateway Interface，或者 Python Web Server Gateway Interfacee，，是一種協議規範。它定義了 Web 伺服器與基於 Python 的應用程式之間的的接口。換句話說，WSGI 為 Web 應用和 Web 伺服器提供了一種通用的語言，使它們能夠相互理解和溝通。 

<font size=2.5px color=#808080> 補充：[PEP 333](https://peps.python.org/pep-0333/) 是 Python 的一個提案，提出 WSGI 的規範，促使 Python 在 Web 開發領域的應用和發展。</font>

#### 🔹 WSGI 和 WSGI server有不一樣嗎？

WSGI 跟 WSGI server 這兩個名詞常常會搞混。
- WSGI 是協議規範。
- WSGI server 是遵照 WSGI 規範的 server，像是 Gunicorn, uWSGI。

![Gunicorn的官網介紹也說明是 Python WSGI server](https://r2.easyimg.io/bh8mgaun3/截圖_2024-04-02_下午6.36.23.png)

#### 🔹 為什麼需要Guicorn ?

當我們使用 Flask 或 Django 這樣的 Web 框架開發應用時，通常會借助於框架提供的簡易伺服器來快速啟動和運行開發環境。但這些內建的伺服器真的適合生產環境嗎？
> 注意： 使用 Flask 框架內建的伺服器時，常常會看到一個警告，提醒我們它主要是為了開發目的而設計的。

![使用 Flask 框架內建的伺服器，可以看到Ｗarning](https://r2.easyimg.io/fyrunws04/development_server.png)

這是因為內建的伺服器缺乏處理大量連線的能力。這時，Gunicorn 就扮演了重要的角色。作為一個遵循 WSGI 協議的伺服器，Gunicorn 不僅提供了更強大的性能和靈活性，還能夠確保應用在生產環境下的穩定運行。

#### 🔹 為什麼又需要 Nginx ?

Nginx 可以提高 Web Server 提高網站效率和處理請求的能力：

- 緩存：幫助“存放”網站上經常使用的資料（比如圖片、CSS 樣式表和 JavaScript 檔案），讓使用者訪問網站時能快速獲得這些資料，減少了等待時間和網絡流量消耗。
- 負載平衡：想象一個超市開設了多個收銀台來應對高峰期的客流量，Nginx 確保每個伺服器都能在承受能力範圍內工作，可以加速響應時間，提高用戶體驗。
- 反向代理：扮演中間人角色，幫助處理和分配來自外部的請求到內部的一個或多個伺服器，增加了額外的安全層，因為外部請求並不直接與內部系統互動。

✏️ 總結：
- WSGI 確保 Python web伺服器能在能運行時更穩定。
- Nginx 透過緩存和反向代理提高訪問速度和處理能力，同時增加安全保護。


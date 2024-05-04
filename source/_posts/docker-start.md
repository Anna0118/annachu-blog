---
title: 在 Mac 安裝 Docker
date: 2024-05-04 17:55:12
tags:
    - docker
categories: Docker
---

教你在 MacOS 安裝 Docker 簡單幾步驟就能成功...

<!-- more -->

![官網寫 Missing 很貼切](https://i.postimg.cc/YSSTJDpP/2024-05-04-6-18-19.png)


身為 Mac 的使用者，在下載 App 時，就會選擇 MacOS Desktop 版，然後進行一系列的手動操作來完成下載。

大多時候會用 Homebrew 來安裝，好處在於它能夠幫助你更有效地管理 macOS 上的應用程式或套件。此外，它還能提供一些尚未支持 macOS 但在 Linux 上可用的配方（Formulae），擴展更多選擇。


以下步驟將帶你一步步安裝 Docker:


#### 1. 先在 MacOS 安裝 Homebrew

#### 2. 透過 Homebrew 安裝 Docker
```cmd
$ brew install --cask docker
```

>為什麼要用 cask 呢？
>
>brew cask 是 brew 的其中一個套件，主要是可以透過 homebrew 的 API 來安裝許多 MAC 的 GUI 軟體，所以安裝成功後，可以在 Applicationsa 目錄看到，就像過往將 App 拖曳到 Application 資料夾底下手動安裝的方式，只是幫你省去了這一段！

![安裝成功](https://i.postimg.cc/tTLBrpCX/2024-05-04-6-58-41.png)

#### 3. 到 Applicationsa 打開 Docker

![第一次打開時會需要你的作業系統密碼，以及需要會員註冊登入](https://i.postimg.cc/MpDrzCtD/2024-05-04-5-58-05.png)

#### 4. Docker Desktop

![目前 Containers 和 Images 是空的](https://i.postimg.cc/8kZ5rccQ/2024-05-04-7-09-16.png)


以上，是不是很簡單呢 ?

也可透過 `brew list` 或  `brew list --cast` 列出透過 homebrew 安裝的套件或App

![使用 brew list --cast 來查看](https://i.postimg.cc/0NYh3VBg/2024-05-04-7-23-27.png)

<hr>

#### 我的環境
> macOS Sonoma 14.4.1
> Homebrew 4.2.20

References:
- 想要更多 homebrew 更多指令，可以查看 [PJCHENder-Homebrew筆記](https://pjchender.dev/app/homebrew/)
- 可以從 [Homebrew cast](https://formulae.brew.sh/cask/) 查看有興趣的 Application

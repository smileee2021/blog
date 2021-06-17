---
title: 免費架設 Blog：使用 Hexo + GitHub Page
tags: Hexo, blog, 部落格, GitHub Page
---

# 前言

> Hi, 這裡是 Smileee 的 Blog，一個樂於分享知識的平台

一談到 Blog 的架設，你會想使用什麼平台？

WordPress？ Wix？ 還是 Webbly？

嘿嘿...我會選擇 Hexo！

---

# 什麼是 Hexo？
Hexo 是一個 <u>靜態網站產生器（Static Site Generator）</u>，也是一個基於 Node.js 所開發的網誌框架

它可比你想像中的還要讚！
- 完全免費
- 主題多樣
- 快速建立 blog
- 擁有中文相關資源
- 支援 Markdown 語法，撰寫文章更方便

只需要幾分鐘，你就可以利用 Hexo 這個工具，將屬於自己的網誌上線！

> ---「架設專屬於自己的 Blog」，聽起來就超酷的 ( • ̀ω•́ ) 

---

# 安裝 Hexo
## 安裝 Hexo 前
在安裝 Hexo 之前，請先安裝下列的項目
- [Node.js 長期維護版（LTS）](https://nodejs.org/zh-tw/)
- [Git](https://git-scm.com/downloads)

## 安裝 Hexo

打開你的 CMD（Windows OS） / Termial（Linux OS or Mac OS），並輸入指令：

```bash
$ npm install hexo-cli -g # 安裝 hexo
$ npm install hexo-deployer-git
```

```bash
$ hexo init <ProjectName> # 建立並初始化 Hexo blog，通常我會將 <ProjectName> 命名為 blog，也就是 hexo init blog
$ cd <ProjectName> # （將路徑）移動至 ProjectName 資料夾
$ npm install # 安裝所需套件
```

---

## 將 Hexo Blog 架設至 GitHub Page
進入 [GitHub 官網](https://github.com) 並創建帳號或登入（登入後的畫面如下圖）

點擊 New repo（Repository 的簡稱，可以理解為 Project）的按鈕（下圖紅框處）：

![GitHub 登入後的頁面、點擊 New Repository 按鈕](https://i.imgur.com/ytho4A0.png)

為 repo 取一個名字！

（由於我已經有建立過名為 blog 的 repo，所以我將新的 repo 名稱命名為 blog-test）

並移動至頁面最下方，點擊 Create repository 按鈕（下方第二張圖的紅框處）

![命名 GitHub repo](https://i.imgur.com/PJAhU1b.png)
![新增 GitHub repo](https://i.imgur.com/bqAUMsz.png)

### 將 blog 部署至 GitHub

在建立 repo 後，會進入如下圖的頁面

於紅框處點選 HTTPS 按鈕並按下右方的複製 URL 按鈕

![](https://i.imgur.com/Fdqqux9.png)

打開剛才建立的資料夾，會找到一個 `_config.yml` 的檔案

並將以下的設定資訊輸入（或修改）至檔案中
```yaml
# <YourUserName> 為你在 GitHub 上的 user name
# <RepoName> 為你剛剛建立的 repo 名稱

url: https://github.com/<YourUserName>/<RepoName>
root: /<RepoName>/

deploy:
  type: git
  repository: https://github.com/<YourUserName>/<RepoName>.git # 修改為剛才複製的 URL，如 https://github.com/smileee2021/blog-test.git
  branch: main
```

在使用 Git 前，我們需要做一些設定：

打開 cmd / terminal 並輸入下列指令

```bash
$ git config --global user.name <YourName> # 將 <YourName> 改為你的名字，如 smileee2021
$ git config --global user.email <YourEmailAddress> # 將 <YourEmailAddress> 改為你的信箱，如 smileee2021@gmail.com
```

在 cmd 上輸入下列指令，就可以將 blog 部署到 GitHub 上啦！

```bash
hexo deploy -g
```

打開 GitHub 確認資料有上傳如果在 GitHub 的 repo 上有看到資料更新

### 開啟 GitHub Pages 功能

點擊 GitHub repo 專案的 settings 按鈕，如下圖紅框處

如果你找不到 settings 在哪裡，可以在瀏覽器打上下列的網址

`https://github.com/{YourName}/{RepoName}/settings`

（{YourName} 為你的名字，{RepoName} 為 Repo 的名稱，例如：https://github.com/smileee2021/blog-test/settings）

![](https://i.imgur.com/ugVQlhy.png)

並點擊左方側邊欄的 Pages，如下圖紅框處

![](https://i.imgur.com/dBLDrGA.png)

然後依序點選 None、main（如下列第一張圖）和 Save（如下列第二張圖）

![](https://i.imgur.com/FARtwbz.png)

![](https://i.imgur.com/yHpIhhp.png)

點選 Save 後，頁面會呈現如下圖，而紅框處中的網址就是你的 blog 啦！

（記得等幾分鐘後，blog 頁面才會正常顯示喔！）

![]( https://i.imgur.com/HJ6rkHA.png)

---

現在，你已經有了自己的一個 blog 了！

接下來，就讓我們繼續看怎麼設定主題和撰寫文章！

（文章連結）
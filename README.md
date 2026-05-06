# Git & GitHub

# 目錄
- [頁首](#git--github)
- [Git&Github介紹](#gitgithub介紹)
- [檔案紀錄](#檔案紀錄)
- [初始化與第一次上傳](#初始化跟第一次上傳)
- [日常三步驟](#日常三步驟)
- [取消commit包含遠端](#取消commit包含遠端)
- [分支操作](#分支操作)
- [在另一台裝置接續開發](#在另一台裝置接續開發)

# Git&Github介紹

版本控制 (Version Control)

## Git

在軟體開發過程中，版本控制 (Version Control) 扮演核心角色。Git 作為分散式版本控制系統，不僅能記錄程式碼的歷史，更能讓團隊在不同分支上同時開發，最後再合併成果。 

透過 Git，我們能：
- 追蹤變更：每一次提交 (commit) 都能保存當下的程式碼狀態。

- 管理分支：開發新功能、修復錯誤，都可以在獨立分支上進行，降低衝突風險。

- 靈活協作：開發者能推送 (push) 程式碼至遠端，透過Pull Request 進行程式碼審查(Code Review)，確保品質並促進協作。

## GitHub

GitHub 不僅是程式碼倉庫，也是一個協作平台。除了版本控制，它還提供Issue 管理、專案看板、CI/CD 整合 (GitHub Actions) 等功能，使團隊能在同一平台上完成從開發到部署的流程。

# 檔案紀錄

## 活動公告

[技術分享公告](./技術分享.pdf)

## 活動錄影

https://youtu.be/zfXo3YreHB4

# 初始化跟第一次上傳

## Git 倉庫初始化 & 第一次提交

### Windows
在 https://git-scm.com 下載並且安裝

or

### Macs
Homebrew:
```bash
brew install git
```

or

- MacPorts:

```bash
sudo port install git
```

## 檢查是否安裝 & 檢查安裝版本

```bash
git --version
```

## 本地資料夾初始化

```bash
git init
```

# 建立遠端Github 倉庫

## 建立新資料

進行上傳前需要專案有變化(建立新檔案、修改檔案)

在資料夾內新增一個 README.md

觀察在建立完之後檔案名有沒有顏色變化

新建立的會是藍色(Untracked)

![文件狀態](./img/file_status.png)

修改過的是橘色(Modified)

## 建立遠端Github 倉庫

登入Github

點選畫面左邊綠色的New
![新倉庫](./img/repo_new.png)

幫新倉庫取名字(取名很重要，要想一下)
可以用的名字會在下方綠色提醒(123 is available.)

![取名字](./img/repo_name.png)

其他不用動按建立倉庫
![建立倉庫](./img/repo_create.png)

## 連接遠端Github倉庫
建立好倉庫會在倉庫主頁看到這塊藍色的區域
將右邊HTTPS的部分複製起來
![獲取連結](./img/repo_url.png)

![獲取連結](./img/repo_url.png)

將下面的 [空格後貼連結] 替換成剛剛複製的倉庫連結

git remote add origin [空格後貼連結]

```bash
git remote add origin
```

## 加入所有變更

```bash
git add .
```

## 提交變更至本地版本庫

實作專案的時候請把 What did you do. 改成這次的更新做了什麼
```bash
git commit -m "Connect project to remote Git repository."
```

## 把目前所在的分支（通常是 master）改名為 main

```bash
git branch -M main
```

## 初次推送並設定 Upstream

```bash
git push -u origin main
```

# 日常三步驟

```bash
git add .
```

```bash
git commit -m "Type what you did."
```

```bash
git push
```

# 取消commit包含遠端

## 找到你想要挑的 commit ID

```bash
git log --oneline
```

## 回到上一個 commit

取消最後一次 commit，但保留修改

```bash
git reset --soft HEAD~1
```

取消最後一次 commit，但保留檔案變更（未暫存）

```bash
git reset --mixed HEAD~1
```

整個回到上個版本，檔案內容也復原

```bash
git reset --hard HEAD~1
```

## 覆蓋遠端

- 沒改寫歷史（沒有 rebase/ amend/ reset）：

- 用 一般 push。

```bash
git push
```

- 剛做完 rebase / amend / reset，需要更新遠端：

- 優先 --force-with-lease。

```bash
git push origin main --force
```

- 個人倉庫或臨時分支，只有你一個人用：

- 可接受 --force
- 但仍建議習慣 
--force-with-lease。

```bash
git push --force-with-lease
```

# 分支操作

## 查看所有分支

```bash
git branch -a
```

## 新增新分支並且讓其追蹤遠端分支

```bash
git switch --track origin/New_branch
```

## 切到你想要去的分支

```bash
git switch main
```

## 刪除已不存在的遠端分支(當遠端刪除分支)

```bash
git fetch -p
```

## 刪除本地分支

```bash
git branch -d 分支名
```

## 強制刪除本地分支

```bash
git branch -D 分支名
```

## 抓遠端最新

- 只同步遠端資訊

```bash
git fetch
```

- 更新當前分支（自動合併，可能多一個 commit）

```bash
git pull
```

- 更新當前分支（線性歷史，乾淨）

```bash
git pull --rebase
```

# 在另一台裝置接續開發

如果我們需要在「另一個裝置」上繼續開發我們已經建立好、更新過的repo，可以使用以下操作接續開發

## 檢查是否安裝 & 檢查安裝版本

```bash
git --version
```

## 在新裝置新增資料夾

這個資料夾是要放置複製下來的專案

所以等一下複製下來的下一層才是repo

以如下格式進行repo的克隆，把遠端的repo複製下來

git clone https://github.com/你的帳號/你的repo.git

```bash
git clone
```

等待克隆完成，接下來查看所有分支

```bash
git branch -a
```

你會看到：
- remotes/origin/main
- remotes/origin/***

如果要切換到你上次所使用的分支

可以按照下面的格式在本地建立分支並追蹤遠端

前面是本地後面是遠端

git switch -c *** origin/***

```bash
git switch -c 
```

最後檢查一下所有分支就可以繼續更新了

```bash
git branch -a
```

請務必確認好你在所想的分支上在進行更新
# Git & GitHub #
## 在軟體開發過程中，版本控制 (Version Control) 扮演核心角色。Git 作為分散式版本控制系統，不僅能記錄程式碼的歷史，更能讓團隊在不同分支上同時開發，最後再合併成果。 ##

## 透過 Git，我們能：
- 追蹤變更：每一次提交 (commit) 都能保存當下的程式碼狀態。
- 管理分支：開發新功能、修復錯誤，都可以在獨立分支上進行，降低衝突風險。
- 靈活協作：開發者能推送 (push) 程式碼至遠端，透過Pull Request進行程式碼審查 (Code Review)，確保品質並促進協作。

## GitHub不僅是程式碼倉庫，也是一個協作平台。除了版本控制，它還提供 Issue管理、專案看板、CI/CD 整合 (GitHub Actions) 等功能，使團隊能在同一平台上完成從開發到部署的流程。 ##



### Git repo init & 1st upload ###
Download and install git at https://git-scm.com
```bash
git init
```
```bash
git remote add origin https://github.com/你的帳號/你的repo.git
```
```bash
git add .
```
```bash
git commit -m "What did you do"
```
```bash
git branch -M main
```
```bash
git push -u origin main
```



### Reroll ###
#### 找到你想要挑的 commit ID ####
```bash
git log --oneline
```

#### 回到上一個 commit ####

```bash
git reset --soft HEAD~1
```
```bash
git reset --hard HEAD~1
```

#### 覆蓋遠端 ####
```bash
git push origin main --force
```



### Branch operation ###
#### 查看目前遠端追蹤分支 ####
```bash
git branch -r
```

#### prune 掉已不存在的遠端分支 ####
```bash
git fetch -p
```

#### 刪除本地分支 ####
```bash
git branch -d 分支名
```

#### 強制刪除本地分支 ####
```bash
git branch -D 分支名
```

#### 切到你想要加進去的分支 ####
```bash
git switch main
```

#### 抓遠端最新 ####
```bash
git fetch
```

#### 建立並切換 ####
```bash
git switch --track origin/feature/login
```



### 📮 To update ###
```bash
git add .
```
```bash
git commit -m "Type what you did"
```
```bash
git push
```
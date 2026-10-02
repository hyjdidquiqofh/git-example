# git branch怎麼用

`git branch` 用於管理、建立、檢視與刪除 Git 版本控制中的分支。

### 1. 查看分支

* **`git branch`**：列出所有本地分支（前面有 `*` 號者為目前所在分支）。
* **`git branch -a`**：列出所有本地分支與遠端（Remote）分支。
* **`git branch -v`**：顯示各分支最後一次 Commit 的詳細訊息。

---

### 2. 建立與切換分支

* **`git branch <分支名稱>`**：建立新分支（建立後仍留在當前分支）。
* **`git switch -c <分支名稱>`** 或 **`git checkout -b <分支名稱>`**：建立新分支並立即切換過去。
* **`git switch <分支名稱>`** 或 **`git checkout <分支名稱>`**：切換到已存在的分支。

---

### 3. 重命名分支

* **`git branch -m <新分支名稱>`**：修改當前所在分支的名稱。
* **`git branch -m <舊分支名稱> <新分支名稱>`**：修改指定分支的名稱。

---

### 4. 刪除分支

* **`git branch -d <分支名稱>`**：刪除已合併的分支（安全刪除）。
* **`git branch -D <分支名稱>`**：強制刪除分支（即使尚未合併）。
* **`git push origin --delete <分支名稱>`**：刪除伺服器上的遠端分支。

---

### 5. 基本開發流程範例

1. **建立並切換至開發分支**
```bash
git switch -c feature/user-login

```


2. **開發完成並提交程式碼後，切換回主分支**
```bash
git switch main

```


3. **將開發分支合併至主分支**
```bash
git merge feature/user-login

```


4. **清理已完成任務的分支**
```bash
git branch -d feature/user-login

```

`git checkout -b <分支名稱>` 是 **`git branch`（建立分支）** 與 **`git checkout`（切換分支）** 這兩個指令的快捷組合。


# git checkout -b 和branch有何關係

### 兩者關係拆解

執行：

```bash
git checkout -b feature

```

完全等同於依序執行以下兩條指令：

```bash
git branch feature    # 1. 建立名為 feature 的分支
git checkout feature  # 2. 切換到 feature 分支

```

---

### 功能差異比較

| 指令 | 作用 | 執行後所在分支 |
| --- | --- | --- |
| `git branch <分支名稱>` | **僅建立**分支 | **停留**在原本的分支 |
| `git checkout -b <分支名稱>` | **建立並切換**至新分支 | **移至**剛建立的新分支 |

---

### 補充：現代 Git 的替代語法

在 Git 2.23 版本之後，官方為了釐清 `checkout` 過於複雜的功能，推出了分工更明確的指令：

* `git branch feature` ＋ `git switch feature`
* **快捷指令**：`git switch -c feature`（`-c` 代表 create，效果完全等同於 `git checkout -b feature`）
需要使用的工具

1. Node.js

2. npm

3. PicGo

4. GitHub

5. Typora

   **Node.js ：**是為了安裝和運行**PicGo** 工具而需要的基礎環境，運用其中的包管理工具**npm**執行命令安裝 **PicGo **。

   **PicGo**：是一個圖片上傳工具，通過 **PicGo ** 上傳圖片到 **GitHub**

   **GitHub**：在這裡充當圖床的角色，使用 **PicGo ** 的 **GitHub**插件，上傳圖片

   **Typora**：是一個 **Markdown** 編輯器，支持圖像上傳功能。透過設定使用 **PicGo** 上傳到 **GitHub**，並自動更新圖片鏈接。

以下是使用 PicGo 命令行版本上傳圖片到 GitHub 的完整步驟：

# 1. 安裝 Node.js 和 PicGo

如果你還沒有安裝 Node.js 和 PicGo，請確保你完成以下步驟：

- **安裝 Node.js**：

  1. 前往 [Node.js 官方網站](https://nodejs.org/) 下載並安裝最新版本的 Node.js。

  2. 安裝後，使用命令行檢查 Node.js 是否安裝成功：

     ```bash
     node -v
     ```

     ```bash
     npm -v
     ```

- **安裝 PicGo**： 在命令行中執行以下命令安裝 PicGo：

  ```bash
  npm install -g picgo
  ```

# 2. 獲取 GitHub Personal Access Token

要將圖片上傳到 GitHub，您需要一個 Personal Access Token：

1. 登錄到 GitHub。開一個新的GitHub儲存庫，記得選public，不然其他人看不到圖片。建好後剛剛上面config裡的repo就可填入`[username]/[repo name]`，例如我的是 `AoAoseal/blog`。
2. 前往 **Settings** > **Developer settings** > **Personal access tokens**。
3. 點擊 **Generate new token**，隨意給個token名字，下面勾選repo，就可以產生token了。
4. 生成並保存這個 Token。 目前我設定到2024/11/30失效

# 3. 配置 PicGo

1.產生config

```bash
picgo set uploader
```

```
? Choose a(n) uploader (Use arrow keys)
  smms
  tcyun
❯ github
  qiniu
  imgur
  aliyun
  upyun
(Move up and down to reveal more choices)
```

1. 選擇github
2. 輸入`[username]/[repo name]` 
3. 分支 可以不選 ENTER跳過
4. 儲存路徑 可以跳過
5.  token 就是剛剛GitHub最後一步的那串 
6. 網域可以跳過

![picGo](https://raw.githubusercontent.com/AoaoSeal/blog/main/picGo.png)

7.以上內容都可以到C:\Users\User\.picgo\config,jason 修改(Windons路徑)或是用命令視窗打指令修改

# 4.Typora

1.偏好設定

![TyporaPic1](https://raw.githubusercontent.com/AoaoSeal/blog/main/TyporaPic1.png)

2.圖片>選擇PicGo-Core (這裡可以下載但我來不及了，下次再試試)

可以點Test測試看看是否成功

![TyporaPic2](https://raw.githubusercontent.com/AoaoSeal/blog/main/TyporaPic2.png)

3.接下來只要對上傳到Typora的圖片右鍵點擊Upload Image就能上傳圖片至github，並且自動將Typora上圖片網址改為從github獲取，也可以使用介面中的選單改成自動上傳圖片

![](https://raw.githubusercontent.com/AoaoSeal/blog/main/TyporaPic3.png)
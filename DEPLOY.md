# 部署步驟（git CLI）

新版時間軸地圖已準備好，需上傳到 leeantonio2023/pongso-no-tao 這個 GitHub repo。

## 內容總覽

- `index.html` — 新版地圖（16 MB，含 1370 個內嵌縮圖）
- `photos/` — 1370 張高解析（1024px）照片+影片首格（共 192 MB），lightbox 放大用
- `videos/` — 55 個壓縮後影片 720p H.264（共 89 MB）
- 總大小：約 297 MB

## 在 Windows PowerShell / 終端機執行

```powershell
# 1. 進入這個資料夾
cd "C:\2023資管系\計畫\114\科博館文教基金會_蘭嶼計畫\cowork_璀璨蘭嶼\pongso-no-tao-new"

# 2. 初始化 git 並連到 GitHub repo
git init
git remote add origin https://github.com/leeantonio2023/pongso-no-tao.git
git branch -M main

# 3. 設定 git 大檔處理（避免單檔超過 100MB 上限；目前最大檔 16MB OK）
git config http.postBuffer 524288000

# 4. 加入所有檔案並推送（會覆蓋現有的 index.html）
git add .
git commit -m "更新 0507-0513 踏查資料：1370 媒體（含 55 影片）+ 高解析 lightbox"
git push -f origin main
```

如果 `git push` 要登入，會跳出 GitHub credential manager 視窗，輸入 GitHub 帳號密碼或 Personal Access Token。

## 推送之後

- GitHub Pages 會在 1-3 分鐘內自動部署
- 網址：https://leeantonio2023.github.io/pongso-no-tao/

## 改進重點

1. **照片放大解析度** — Lightbox 現在會載入 `photos/<檔名>` 外部 1024px 高解析 JPEG（原本只有 220px base64 縮圖，所以模糊）。
2. **影片支援** — 地圖上的紅色實心圓圈 = 影片；點開 lightbox 會用 `<video>` 播放器播 720p 壓縮版本。
3. **7 天時間軸** — 5/7、5/8、5/9、5/10、5/11、5/12、5/13 全部分日篩選。

# 這堂課值得上嗎

一頁式工具：填四格（課程網址、你的背景、想解決的問題、預算），一鍵把「課程盡職調查」的 prompt 送進 ChatGPT、Gemini、Claude 或 Perplexity，用它們的免費額度去 PTT、Dcard、Threads、方格子、YouTube 留言翻真實心得，最後給出買／不買的明確結論。

## 特色

- **證據分級 A/B/C/D** — 強制 AI 標示每則引用的可信度，廠商官網的「學員見證」一律降為 D 級，不得當作口碑證據。
- **誠實規範** — 找不到負評就直說找不到並解釋原因，不准用「整體評價正面」填補資料空白，不准編造連結。
- **紅旗清單** — 八項線上課程消費爭議最常見的模式，逐項標示 ✅／⚠️／🚩。
- **兩種長度** — 完整版（複製後貼上）與精簡版（可直接塞進網址，ChatGPT / Claude / Perplexity 會自動帶入問題）。

## 部署到 GitHub Pages

```bash
git init
git add .
git commit -m "課程盡職調查工具"
gh repo create course-check --public --source=. --push
gh api -X POST repos/:owner/course-check/pages -f "source[branch]=main" -f "source[path]=/"
```

或在 GitHub 網頁上：Settings → Pages → Source 選 `main` / `root`。

網址會是 `https://<你的帳號>.github.io/course-check/`。

## 檔案

單一 `index.html`，沒有建置流程、沒有相依套件。字型從 Google Fonts 載入，其餘全部內嵌。

## 自行修改

- Prompt 內容在 `index.html` 底部的 `buildFull()` 與 `buildLite()` 兩個函式裡。
- 要加平台，在 `TARGETS` 物件裡加一筆；`param` 填該站接收問題的 query 參數名稱，沒有就填 `null`（按鈕會改成「複製後貼上」）。
- 配色 token 全部在 `:root` 區塊，深色主題在下面兩個區塊各覆寫一次。

## 授權

隨你用，改了拿去分享也可以。

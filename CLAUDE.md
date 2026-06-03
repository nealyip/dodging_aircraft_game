# CLAUDE.md

呢個 repo 嘅指引，俾 Claude Code（同其他 AI agent）跟住做。

## 專案概覽

「彈幕避彈 — 飛機閃子彈」：單檔 HTML5 Canvas 彈幕避彈小遊戲，零依賴、無建置步驟。

- `dodge.html` — 全部遊戲邏輯（HTML + CSS + JS 都喺呢一個檔案）
- `index.html` — 自動跳轉去 `dodge.html`，俾 GitHub Pages 根網址用
- 線上版：<https://nealyip.github.io/dodging_aircraft_game/>（push 上 `main` 自動部署）

## 版本規則（每次 commit 必做）

版本號定義喺 `dodge.html` 入面：

```js
const VERSION = 'x.y.z';   // 顯示喺開始頁
```

採用語意化版本 `MAJOR.MINOR.PATCH`。**每次 commit 都一定要 bump 版號**，規則如下：

- **修 bug / fix** → 升 **PATCH**（第三位）：`1.0.0` → `1.0.1`
- **新功能 / feature update** → 升 **MINOR**（第二位），PATCH 歸零：`1.0.1` → `1.1.0`
- **破壞性大改 / 重寫** → 升 **MAJOR**（第一位），MINOR、PATCH 歸零：`1.1.0` → `2.0.0`

做法：

1. 改完功能後，更新 `dodge.html` 入面 `const VERSION` 嘅值。
2. 喺同一個 commit 一齊提交（版號改動同實際改動唔好分開 commit）。
3. Commit message 開頭可以帶版號，例如：`v1.0.1: fix start button ...`。

> 由 `1.0.0` 開始。如果唔肯定改動算 fix 定 feature，傾向當 feature 升 MINOR。

## Commit / Push 慣例

- Commit message 用祈使句、講清楚做咗咩同點解。
- 結尾加：`Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>`
- 只喺 `main` branch 開發、直接 push。

## 開發備註

- 改完 `dodge.html` 之後，最少做一次語法檢查：
  ```bash
  node -e "const s=require('fs').readFileSync('dodge.html','utf8');const m=s.match(/<script>([\s\S]*)<\/script>/)[1];new Function(m);console.log('JS syntax OK')"
  ```
  `new Function` 只驗語法，捉唔到 runtime 錯（例如 const 嘅 temporal dead zone）；改動較大時最好用 DOM shim 真正執行一次。
- 手機操控用畫面下方獨立搖桿盤（`#pad`），1:1 相對拖動；桌面用滑鼠／WASD／方向鍵。
- 離開分頁／失焦會暫停計時（`visibilitychange` / `blur`），避免計時跳秒。

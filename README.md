# 彈幕避彈 — 飛機閃子彈

一個單檔 HTML5 Canvas 彈幕避彈小遊戲。操控飛機，閃避從四方八面射埋嚟嘅子彈，撐得越耐越勁，難度會逐漸提升。

## 玩法

- **電腦**：WASD / 方向鍵 或 滑鼠移動
- **手機**：用畫面下方嘅虛擬搖桿盤（喺遊戲範圍外，手指唔會擋住畫面）拖郁，飛機 1:1 跟手指位移移動
- 被任何子彈擊中即遊戲結束
- 飛機中心嘅細紅點先係真正受擊範圍，方便擦彈

按 `Space` / `Enter` 開始或重新開始。

## 線上試玩

透過 GitHub Pages：<https://nealyip.github.io/dodging_aircraft_game/dodge.html>

## 本地執行

直接用瀏覽器開 `dodge.html` 即可，無需任何依賴或建置步驟。

## 技術

- 純前端、零依賴、單一 `dodge.html`
- HTML5 Canvas 繪圖 + `requestAnimationFrame` 主迴圈
- 離開分頁／視窗失焦時會自動暫停計時，避免計時跳秒
- 最佳紀錄以 `localStorage` 保存

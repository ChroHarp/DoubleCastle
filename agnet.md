# agnet.md

## 專案簡介
這是單頁版的瀏覽器棋盤遊戲（目前為 1～12 的可調棋盤大小），以純前端 HTML/CSS/JS 實作，介面使用 Tailwind CDN。遊戲包含人機與雙人對戰模式、先手選擇、可復原一步、全螢幕切換、即時計算合法/淘汰格數。

## 目錄與檔案
- `index.html`：所有 UI、樣式與遊戲邏輯都在此檔案內（無額外 build 步驟）。
- `README.md`：簡短說明。

## 遊戲核心規則（程式邏輯）
- 棋盤以 `BOARD_SIZE` x `BOARD_SIZE` 的 2D 陣列 `boardState` 表示，0 為空格，1/2 為玩家棋子。
- 合法落子：該格為空且「同行已有棋子數 + 同列已有棋子數 < 2」。
- 合法步數為 0 則遊戲結束，當前玩家為落子方，勝者為另一方。

## 重要 UI/互動
- 電腦對戰切換：`#ai-toggle`（預設關閉）。
- 先手切換：`#first-player-toggle`（AI 模式才可用）。
- 棋盤大小滑桿：`#board-size-slider`（目前上限 12）。
- 主要事件：`handleCellClick`、`makeAIMove`、`handleUndo`、`toggleFullScreen`。

## 常見修改點
- 若要改變棋盤大小上限/預設值：修改 `#board-size-slider` 的 `min/max/value`。
- 若要改變 AI 行為：修改 `makeAIMove()`（目前為隨機合法步）。
- 若要調整勝負判定或規則：修改 `isValidMove()` 與 `checkGameOver()`。

## 開發與驗證
- 直接用瀏覽器開啟 `index.html` 即可運行。
- 無打包工具、無後端依賴。


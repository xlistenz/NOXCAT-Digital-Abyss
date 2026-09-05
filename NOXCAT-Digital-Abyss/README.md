# NOXCAT-Digital-Abyss

可直接開啟 `index.html` 的單檔前端 Canvas 平台遊戲。沒有套件、伺服器、帳號或網路請求；音效使用瀏覽器的 Web Audio API 即時產生。

## 啟動與操作

1. 直接雙擊 `index.html`，或把它拖入 Chrome、Edge、Firefox、Safari。
2. 按 **START GAME**；瀏覽器會在此時允許原創音效啟動。
3. 使用 `A/D` 或 `←/→` 移動，`Space` 或 `W` 跳躍。空中再按一次可二段跳。

手機請以橫向開啟遊戲。底部的 `←`、`→`、`JUMP` 按鈕使用 touchstart/touchend，無需鍵盤。

## NOXCAT 素材

原始官方角色圖保留在 `assets/player/noxcat-spritesheet.png`；遊戲目前使用已去除連通深色背景、具透明 alpha 的 `assets/player/noxcat-spritesheet-alpha.png`。`game.js` 的 `Player.draw()` 以 6 欄 × 4 列切割來源圖，依 idle/run/jump/fall/hurt 狀態挑選動畫格；換圖時最好保持此格線，或調整該方法中的 `sw`、`sh` 和 `frame` 對應。

## 製作下一關

在 `game.js` 的 `Level.make()` 內新增 `this.p(x, y, 寬度, 類型)`；可用類型為 `stone`、`metal`、`pulse`、`energy`、`float`、`break`、`bounce`、`hazard`。同一方法也集中定義敵人、能量、Beacon、移動平台與 NOX CORE，適合複製成下一個 `Level` 設定。

## 調整時限

搜尋 `this.time=180`（在 `Game` 建構與 `start()` 各一處），改成所需秒數即可。完成獎勵依目前剩餘秒數乘以 10 計算。

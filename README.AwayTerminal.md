# AwayTerminal

Windows 原生終端機模擬器。分頁 / 分割畫面、PowerShell、SSH、Telnet、序列埠(COM)、ADB、自訂連線，
並支援 Telegram 遠端控制、巨集、記錄檔。

- 原始碼：https://github.com/awaysu/AwayTerminal
- 下載頁總覽：[README.md](./README.md)

## 安裝檔

| 檔案 | 版本 | 大小 | SHA256 |
|---|---|---|---|
| [`AwayTerminal-Setup-1.0.20.exe`](./AwayTerminal-Setup-1.0.20.exe) | 1.0.20 | 61.8 MB | `3085EAAAD4CA5D9D77399C9AA2CDD7DB8EEC5580FF0AC49CDBAD896D225256D2` |
| [`AwayTerminal-Setup-1.0.11.exe`](./AwayTerminal-Setup-1.0.11.exe) | 1.0.11 | 55.6 MB | `BF232C9227DE6979566AA349AE36AFC2E8626901B3FA0841FDF29632A1335083` |
| [`AwayTerminal-Setup-1.0.10.exe`](./AwayTerminal-Setup-1.0.10.exe) | 1.0.10 | 55.6 MB | `A5AE533C1E29F2C8EED502AD88FDEC6C51F41809A4CFD3CA47F247C3D78A4C95` |

## v1.0.12 ~ v1.0.20 更新內容

**安裝與體積**

- 改為**框架相依**發佈：安裝後磁碟佔用由 184.8 MB 降到 **7.4 MB**。安裝檔內含 .NET 9 Desktop
  Runtime，僅在你的電腦沒有時才安裝；之後 .NET 的安全性更新改由 Windows Update 維護
- 升級時會清掉舊版殘留的執行環境檔案，不再逐版堆積

**授權與安全**

- 加入 **MIT 授權**與第三方聲明（`LICENSE`、`THIRD-PARTY-NOTICES.md`，隨程式一起安裝）
- **不再打包 Google 的 adb**，改用你電腦上已安裝的 Android SDK Platform Tools
  （自動搜尋 PATH、ANDROID_HOME / ANDROID_SDK_ROOT、Android Studio 預設位置）
- **安裝時不再把憑證匯入系統的「受信任的根」**。想讓 UAC 顯示發行者名稱的人，可自行執行
  安裝目錄下的 `trust-publisher.ps1`（只寫入自己的憑證存放區、不需系統管理員權限）

**功能**

- 終端機右鍵新增「**複製且貼上**」：選取的文字複製後直接貼回終端機
- **Claude Code 多行貼上修正**：不再被拆成好幾段（Windows 10 主控台會丟棄貼上標記，
  改用 Claude 自己的軟換行鍵送出，200 行貼上也完整）
- 「新連接」選單重整：預設區只留 PowerShell／SSH-Telnet／連接埠；**ADB 與其他工具改由
  「自訂…」管理**（可用「自動偵測」一鍵加入），**全新安裝的自訂清單是空的**
- 常用字串換上新的預設範例；範例只在第一次建立設定檔時放入，**刪掉不會再長回來**
- Telegram 遠端降噪：**打字時不再誤推播**「完成」訊息，沒有新輸出時也不再送出空訊息
- 修正部分情況下**資料夾選擇視窗開在主視窗後面**、看起來像「點了沒反應」的問題

## v1.0.11 更新內容

- 終端機右鍵選單「複製」下方新增「**複製且貼上**」：選取的文字複製到剪貼簿後直接貼回終端機，
  想重跑畫面上看到的指令時一步完成

## v1.0.10 更新內容

- Claude Code 分頁多行貼上修正：先前貼多行文字有時會被拆成好幾段（尾端碎片留在輸入框、
  出現「paste again to expand」），Windows 10 的主控台會把貼上標記從輸入流丟掉、
  Claude 只能靠輸入時序猜測所致。改用 Claude 自己的軟換行按鍵送出，200 行貼上也完整不分裂

## v1.0.9 更新內容

- 視窗標題路徑擴大支援：提示行解析新增 RHEL/CentOS（`[user@host dir]#`）、Android adb（`host:/path $`）、
  zsh/fish 等格式，SSH/Telnet/COM 連進的裝置也能顯示目前路徑
- claude／自訂連線分頁（無提示行）改顯示啟動時選的工作目錄，多開專案時一眼分辨

## v1.0.8 更新內容

- 視窗標題顯示目前路徑：`AwayTerminal - C:\目前\路徑`（PowerShell／cmd／SSH 提示行自動解析，cd 後即時更新）
- 終端機右鍵選單改版：貼上／複製／複製全部／複製全部存至檔案／搜尋（Ctrl+F）
- 「複製全部存至檔案」：把整個畫面緩衝區（含 scrollback）存成純文字 .txt
- 多行貼上修正：改走 bracketed paste，貼多行文字不再被逐行當成 Enter 執行（claude／vim／bash 皆正常）
- 注音輸入修正：組字過程不再閃出英文字（如 h）
- 工具列「貼上」改名「純文字貼上」

## v1.0.5 更新內容

- 「關於」視窗改版：內容置左、作者與 Source Code 連結、顯示編譯時間
- Telegram 遠端：inline 按鈕（/list /new /history 選擇題 /close 確認）、只推新輸出、
  /ssh /telnet /history /more /close 指令、10 分鐘閒置自動離開
- SSH/Telnet/COM 斷線自動重連（連線視窗勾選）；SSH/Telnet 保持連線（預設 10 分鐘）
- 同機多開時 Telegram 遠端由第一個視窗獨佔（避免訊息互搶）

## 安裝說明

1. 下載並執行 `AwayTerminal-Setup-1.0.20.exe`。
2. 若跳出「Windows 已保護你的電腦」→ 點 **其他資訊 → 仍要執行**。
3. UAC 出現按 **是**（安裝需系統管理員權限：會安裝程式、匯入自簽憑證、必要時安裝 WebView2 執行環境）。
4. 安裝完成後，程式本體不會再被 Windows 擋。

> 安裝檔已內含 .NET 9 Desktop Runtime，僅在對方電腦沒有時才會自動安裝，不必自行準備 .NET。

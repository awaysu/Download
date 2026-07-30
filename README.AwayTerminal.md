# AwayTerminal

Windows 原生終端機模擬器。分頁 / 分割畫面、PowerShell、SSH、Telnet、序列埠(COM)、ADB、自訂連線，
並支援 Telegram 遠端控制、巨集、記錄檔。

- 原始碼：https://github.com/awaysu/AwayTerminal
- 下載頁總覽：[README.md](./README.md)

## 安裝檔

| 檔案 | 版本 | 大小 | SHA256 |
|---|---|---|---|
| [`AwayTerminal-Setup-1.0.9.exe`](./AwayTerminal-Setup-1.0.9.exe) | 1.0.9 | 55.6 MB | `4F015F81D800390A4D8EF03DC627889344D457D20506233EE5ED372A7C41A295` |
| [`AwayTerminal-Setup-1.0.8.exe`](./AwayTerminal-Setup-1.0.8.exe) | 1.0.8 | 55.6 MB | `F12A5C2EB17C3D2244127D6DE9CCF43E603F28B886400DD22EE7B4FCF63AD420` |
| [`AwayTerminal-Setup-1.0.5.exe`](./AwayTerminal-Setup-1.0.5.exe) | 1.0.5 | 55.6 MB | `C1042B90787D353E604E06BA50B05FCD98D94218E0810D4D8E5A288FE3EAD3E5` |

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

1. 下載並執行 `AwayTerminal-Setup-1.0.9.exe`。
2. 若跳出「Windows 已保護你的電腦」→ 點 **其他資訊 → 仍要執行**。
3. UAC 出現按 **是**（安裝需系統管理員權限：會安裝程式、匯入自簽憑證、必要時安裝 WebView2 執行環境）。
4. 安裝完成後，程式本體不會再被 Windows 擋。

> 內含 .NET 執行環境（self-contained），對方不必另裝 .NET。

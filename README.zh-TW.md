# **でびるコネクショん 通用模組載入器**

[繁體中文](https://github.com/nekodakohaku-dev/DevilConnection_Mod_Loader/blob/main/README.zh-TW.md)  |  [日本語](https://github.com/nekodakohaku-dev/DevilConnection_Mod_Loader/blob/main/README.ja.md)  |  [English](https://github.com/nekodakohaku-dev/DevilConnection_Mod_Loader/blob/main/README.md)

這是一個專為遊戲 **《でびるコネクショん》** 設計的非官方通用模組載入器。

本工具允許玩家在**不解碼、不替換原始巨大檔案**的情況下，透過外部掛載的方式載入 .asar 格式的語言包、修正檔或功能模組。此架構能大幅減少補丁體積，並**更好地保護遊戲作者以及模組創作者的著作權**。

## **✨ 功能特點**

* **非破壞性安裝**：使用 HDiffPatch 技術僅對核心進行微小注入，保留原始檔案備份，隨時可還原。  
* **插件系統**：自動讀取 plugins 資料夾內的 .asar 檔案或資料夾。  
* **優先級管理**：支援多模組同時載入，並可透過檔名控制覆蓋順序。  
* **極輕量化**：核心補丁體積極小，完全不影響遊戲效能。

## **🚀 安裝方法**

請依照以下步驟進行安裝：

1. **下載本專案**  
   * 點擊 GitHub 的 \[Releases\] 下載最新版本的壓縮包。  
2. **下載補丁工具**：  
   * 前往 [HDiffPatch Releases](https://github.com/sisong/HDiffPatch/releases) 下載最新版。  
   * 解壓縮並找到 hpatchz.exe。  
3. **放置檔案**：  
   * 將本專案的檔案 (Loader.js, patch.hdiff, Mod Loader Installer.bat) 以及剛剛下載的 hpatchz.exe，全部複製到遊戲的根目錄下。

**📂 檔案結構示意：**SteamLibrary\\steamapps\\common\\でびるコネクショん\\  
│  
├── Loader.js                \<-- 載入器核心  
├── patch.hdiff              \<-- 核心差異補丁  
├── Mod Loader Installer.bat \<-- 安裝腳本  
├── hpatchz.exe              \<-- 補丁應用工具  
└── DevilConnection.exe      \<-- (原本的遊戲執行檔)

4. **執行安裝**：  
   * 雙擊執行 **Mod Loader Installer.bat**。  
   * 腳本會自動備份原檔並注入 Loader。  
   * 安裝成功後，會自動在遊戲目錄下生成一個 plugins 資料夾。  
5. **完成**：現在您可以開始安裝模組了。

## **📖 使用說明**

### **🟢 基礎應用：安裝模組/漢化**

1. 取得您想要使用的模組檔案（通常是 .asar 格式，例如 zh-tw.asar）。  
2. 將該檔案放入遊戲根目錄下的 **plugins** 資料夾中。  
3. 直接啟動遊戲，模組將會自動生效。

### **🟠 進階應用：多模組優先級**

本 Loader 支援同時掛載多個模組，並依照 檔名排序 (Z \-\> A) 決定優先級。  
數字越大、字母越後面的檔案，優先級越高（會覆蓋前者）。  
範例：  
假設 plugins 資料夾內有以下檔案：

* 01\_Base\_Translation.asar (基礎漢化)  
* 99\_UI\_Fix.asar (介面修正)

載入結果：  
Loader 會先讀取 99\_UI\_Fix.asar，然後再讀取 01\_Base\_Translation.asar。  
如果兩個模組都修改了同一張圖片，遊戲將會顯示 99\_UI\_Fix.asar 裡面的版本。  
這讓您可以輕鬆製作「修正檔」或「相容包」，而不需要重新打包整個漢化檔。

## **⚠️ 注意事項與移除**

* **遊戲更新**：如果 Steam 更新了遊戲，Loader 核心可能會失效。請下載最新版本或重新執行 Mod Loader Installer.bat 即可修復上一版本（腳本會自動處理備份與更新）。  
* **移除 Mod**：只需將 .asar 檔案從 plugins 資料夾移出即可。  
* **移除 Loader**：  
  1. 刪除 Loader.js 和 plugins 資料夾。  
  2. 透過 Steam 驗證檔案完整性，還原 app.asar。  
  3. 或手動將 app.asar 刪除，並且將 app.asar.bak 更名回 app.asar。

## **📅 更新日誌**

* **2025/11/24 (v1.0.0)**  
  * 發布 v1.0.0  
  * 對應遊戲版本：Patch Update (2025/11/22)

## **⚖️ 免責聲明 (Disclaimer)**

本工具為第三方製作的非官方軟體，與原遊戲開發商無任何關聯。  
使用本工具所產生的任何風險（如存檔損壞、遊戲崩潰）需由使用者自行承擔。  
請勿用於盜版遊戲。

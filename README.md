# AutoBild 爬蟲 v11.0

德國 AutoBild 汽車型錄爬蟲系統，自動擷取所有品牌、車系、車型資料。

## 功能特色

- ✅ 自動爬取所有品牌和車系
- ✅ 7天增量更新（重啟後自動跳過已爬取的車系）
- ✅ 自動展開所有變體
- ✅ 嘗試擷取 HSN/TSN
- ✅ 中文翻譯（車型、燃料類型）
- ✅ 自動安裝所需套件
- ✅ CSV 匯出

## 欄位說明

| 欄位 | 說明 |
|------|------|
| Brand | 品牌 |
| Model | 車系 |
| Category | 車型（已翻譯為中文） |
| Fuel_Type | 燃料類型（已翻譯為中文） |
| Typ | 規格名稱 |
| Start_Year | 開始年份 |
| End_Year | 結束年份 |
| HSN_TSN | 型式認證號碼 |

## 使用方式

### 本地執行（Mac/Linux）

```bash
python autobild_v11.py              # 完整掃描
python autobild_v11.py --test       # 測試模式
python autobild_v11.py --brand VW   # 只抓特定品牌
python autobild_v11.py --status     # 查看統計
python autobild_v11.py --reset      # 重置資料庫
```

### Windows

雙擊 `run_autobild.bat` 或執行：

```cmd
python autobild_win.py
```

### GitHub Actions（自動排程）

1. Fork 此仓库
2. 到 Settings → Actions → General
3. 選擇 "Allow all actions"
4. 到 Actions 頁面，手動觸發或等待每週日自動執行

### Google Colab

1. 上傳 `autobild_github.py` 到 Colab
2. 執行腳本即可（會自動安裝套件）

## 檔案說明

| 檔案 | 說明 |
|------|------|
| `autobild_v11.py` | Mac/Linux 版本 |
| `autobild_win.py` | Windows 版本 |
| `autobild_github.py` | GitHub/Cloud 版本 |
| `run_autobild.bat` | Windows 啟動腳本 |
| `requirements.txt` | Python 套件清單 |
| `.github/workflows/autobild.yml` | GitHub Actions 設定 |

## 環境需求

- Python 3.8+
- 所有套件會自動安裝：
  - playwright
  - pandas
  - nest_asyncio

## 輸出

- 資料庫：`autobild_master.db`
- CSV：`AutoBild_Exports/` 目錄下，每個品牌一個檔案

## 注意事項

- 首次執行會自動安裝套件和 Chromium 瀏覽器
- 建議使用 VPN 或代理，避免被封鎖
- 完整掃描約需 3-5 小時
- 7天內重啟會自動跳過已爬取的車系

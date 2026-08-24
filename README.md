# 失控寄抽管理系統

本版已將目前兩份 Excel 匯入邏輯整合：
- `WEI寄抽.xlsx` → 老闆：WEI（4 筆套組、1 筆銷售）
- `益(1).xlsx` → 老闆：益（174 筆套組、156 筆銷售）

## 重要架構更新
- 套組編號不再全域唯一，而是「老闆 + 套組編號」唯一，因此不同老闆可以有相同編號。
- 銷售紀錄會依「老闆 + 編號」連到正確套組。
- 原 Excel 銷售紀錄中出現的 `#NAME?` 品名，匯入時改用對應套組的品名。
- 新增銷售後，Supabase trigger 會自動更新對應套組的總收入、總刮數與毛利。
- 系統仍保留「未分配」老闆，方便日後處理尚未歸屬的舊資料。

## 全新專案安裝
1. 在 Supabase SQL Editor 執行 `supabase.sql`。
2. 在 Supabase 建立登入帳號（Authentication → Users）。
3. 使用 `index.html` 開啟／部署前端。
4. 前端使用 Supabase Project URL + Publishable Key。

## 已有專案更新
若你已經執行過舊版 `supabase.sql`，建議先備份目前資料，再執行 `data_update_WEI_益.sql`。
這個更新檔會建立／更新 `WEI`、`益` 兩位老闆並匯入兩份目前 Excel 資料。

不要把 Service Role / Secret Key 放進前端。

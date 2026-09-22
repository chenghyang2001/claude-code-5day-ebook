# 上架前檢查報告（Preflight）

- 檔案：`release/claude-code-5day-guide-v1.0-googleplay.epub`
- 檢查日期：2026-09-22

## EPUBCheck 5.4.0

```
No errors or warnings detected.
Messages: 0 fatals / 0 errors / 0 warnings / 0 infos
```

## 結構檢查

| 項目 | 結果 |
| --- | --- |
| 可開啟、章節順序正確 | PASS（13 個章節檔：前言、原則、Day 1–5、附錄 A–E、版本資訊） |
| 中文無亂碼（UTF-8） | PASS（Chrome 實際渲染截圖確認） |
| 封面顯示（OPF `cover-image`） | PASS（1600×2560 JPG） |
| 目錄可跳轉（nav.xhtml / toc.ncx） | PASS |
| Metadata（title / creator / lang=zh-TW / publisher） | PASS，與封面、書名頁、上架文案一致 |
| 標題層級一致（H1 章、H2 節） | PASS |
| 表格 | PASS（皆為 2–4 欄小表格） |
| 特殊符號 | 已移除 emoji（✅❌）與 HTML 核取方塊，改用純文字「【建議】【避免】□」避免閱讀器缺字 |

## AI 風險排查（四大雷區）

| 雷區 | 處理 |
| --- | --- |
| 編造平台規則 | 安裝方式、指令皆加註「請以官方最新說明為準」 |
| 編造數據 | 全書無統計數據 |
| 非台灣用語 | 已用台灣繁中用語（檔案、資料夾、使用者、建立） |
| 舊版流程當新版 | 所有 CLI 參數與子指令已對照 `claude --help`（2.1.278）實際輸出 |

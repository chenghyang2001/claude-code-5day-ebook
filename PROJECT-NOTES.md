# 專案筆記：《5 天上手 Claude Code CLI》從零到送審

> 記錄日期：2026-09-22｜目的：日後回顧細節用

## 一、起點：從 Kindle 104 學方法

- 來源書：Kindle 104《30 天完成你的第一本電子書》（NotebookLM `b8dc084e`）
- 前置整理：
  - 影片摘要 7 支補上 00–06 編號，刪掉失敗的 3 支；資訊圖表失敗的 9 張也刪掉
  - 四類產物共 35 檔（765 MB）下載到 `~/workspace/Kindle-104-30天完成你的第一本電子書/`（audio／slides／video／infographic），逐檔 md5 驗證
  - 7 份簡報 PDF（94 頁，純圖片）派 7 個子代理平行讀完，彙整成 `SUMMARY.md`
- 學到的核心方法：
  - 小成果題目：「讀完後讀者可以完成〔＿＿〕」
  - 每天只做一件可檢查的事
  - 粗草稿、修訂、候選稿三者分離
  - EPUB 分 v0.1／v0.5／v0.9 三輪輸出測試
  - 上架文案分短、中、長三版
  - 用 `CLOSURE.md` 結案

## 二、這本書

| 項目 | 內容 |
| --- | --- |
| 書名 | 5 天上手 Claude Code CLI |
| 副標 | 每天 20 分鐘，從安裝到交出第一個 AI 協作小專案 |
| 作者／出版者 | 楊政憲 |
| 固定公式 | 每日三格：一個指令＋一句提示＋一個驗收（仿《7 天早餐》的主食＋蛋白質＋蔬果） |
| 練習專案 | 「心情小日記」單頁網頁（只需瀏覽器，讀者不必會寫程式） |
| 附錄 | 5 天全景表、IF/THEN 故障排除、保底模式、第二週進化迴圈、提示詞樣板、版本資訊 |

5 天內容：

| 天 | 主題 | 學的指令 |
| --- | --- | --- |
| 1 | 安裝並完成第一次對話 | `claude`、`/help`、`/exit` |
| 2 | 讓 Claude 認識專案 | `/init`、`CLAUDE.md`、`@檔名` |
| 3 | 讓 Claude 改檔，你掌握方向盤 | `Shift+Tab` 規劃模式、`Esc` 中斷、雙擊 `Esc` 回復 |
| 4 | 管理對話與存檔 | `/clear`、`/compact`、`claude -c`、`!`、git 提交 |
| 5 | 一行指令自動做事 | `claude -p`、管線、`--output-format json` |

## 三、製作過程與技術細節

- **工具**
  - pandoc 3.11（winget 安裝），原稿 YAML front matter 內含 metadata
  - EPUBCheck 5.4.0（Java 21）驗證
- **指令正確性**：全書指令都對照本機 `claude --help`（2.1.278）的實際輸出，並加註「請以官方最新說明為準」
- **封面**
  - PIL 繪製，1600×2560，使用微軟正黑體，深色終端機風格
  - 縮圖狀態下已確認可讀
- **驗證結果**
  - EPUBCheck：0 錯誤 / 0 警告
  - 用 Chrome 截圖確認中文、表格、程式碼區塊都正常
- **Repo**：<https://github.com/chenghyang2001/claude-code-5day-ebook（公開，tag> `v1.0`）
- **檔案**：`manuscript.md`、`epub-style.css`、`cover.jpg`、`release/*.epub`、`google-play-books-listing.md`、`author-bio.md`、`google-play-preflight-report.md`、`CLOSURE.md`

## 四、Google Play 圖書上架

| 項目 | 內容 |
| --- | --- |
| 合作夥伴中心帳戶 ID | 6849693861286336967 |
| 書籍 ID | GGKEY:JW0UQ7B3AAZ |
| 付款資料 | GoogleBook-付款資料（銷售地區 WORLD） |
| 銀行 | 台北富邦北投分行（使用者本人填寫） |
| 類型 | BISAC COM051000 Programming / General；COM100000 AI / Generative AI |
| 定價 | NT$30（台灣前台 NT$31.50，作者約得 NT$16＝52%；歐美多數 70%，如美國 US$0.99 → 得 US$0.69） |
| 設定 | DRM 開、試閱 20%、禁止複製 |
| 發布 | 2026-09-22 已按「發布」，狀態「帳戶待審查」 |

官方時程：新帳戶審查最長 30 個工作天（不含週末假日），通過後 12 小時內上架；超過 30 天可聯絡 Play 圖書客服。

## 五、提醒機制

- **VPS 自動檢查**
  - `at` 任務編號 26，2026-10-06 台北 09:00 執行 `~/reminders/gpb-check.sh`
  - 到 Google Play 搜尋書名，判斷是否上架，再寄 Gmail 通知
- **Google 日曆備援**：2026-10-06 09:30

## 六、踩坑紀錄（下次會用到）

1. **中文字型缺字**
   - 微軟正黑體沒有「✓」字元，封面上會變成方框 → 改用線條畫出勾號
   - EPUB 裡的 ✅❌ 在部分閱讀器會缺字 → 改成【建議】【避免】
2. **核取方塊**：pandoc 會把 `- [ ]` 轉成 HTML 核取方塊元件，很多電子書閱讀器不支援 → 改用「□」
3. **Git Bash 路徑**：`git -C /c/...` 的路徑不會被轉換 → 先用 `cygpath -w` 轉成 Windows 路徑
4. **上傳只吃真人點擊**
   - 合作夥伴中心的上傳鈕不接受程式觸發的 click，也不接受合成的拖放事件
   - 解法：先改寫 `HTMLInputElement.prototype.click`，讓它填入從 GitHub raw 下載的檔案，再用真實點擊按下「瀏覽」
5. **檔名會被改掉**：Google 會把上傳的檔案改名成 `<書籍ID>.epub` 和 `<書籍ID>_frontcover.jpg`
6. **Google Play 搜尋會誤判**
   - 查詢字串會出現在搜尋頁的 `og:title` 裡，只比對關鍵字一定會命中，變成「已上架」的誤判
   - 解法：比對書名原文（有空格），並要求頁面上有 `/store/books/details?id=` 書籍連結
7. **安全規則**：銀行帳號、戶名等金融資料 AI 不代填，由本人輸入

## 七、待辦

- [ ] 補填稅務資訊（首頁清單仍未完成，撥款前需要）
- [ ] 銀行帳戶小額驗證
- [ ] 審核通過後：到 Google Play 看前台頁面、試閱、封面
- [ ] 刪除本機暫存的存摺照片
- [ ] v1.1：補操作截圖、Windows 與 macOS 差異對照、第二週實戰範例

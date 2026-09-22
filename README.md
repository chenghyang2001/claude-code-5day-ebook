# 5 天上手 Claude Code CLI

![封面](images/cover-thumb.png)

一本給新手的每日行動指南電子書：5 天、每天約 20 分鐘，用固定的「每日三格」公式（一個指令＋一句提示＋一個驗收），在自己的電腦上用 Claude Code CLI 完成一個「心情小日記」小網頁專案。

本書依《30 天完成你的第一本電子書》的方法製作：小成果題目、學習者導向章節、EPUB 三階段輸出、上架交付包與結案紀錄。

## 下載

- EPUB：[`release/claude-code-5day-guide-v1.0-googleplay.epub`](release/claude-code-5day-guide-v1.0-googleplay.epub)

## 專案結構

| 檔案 | 用途 |
| --- | --- |
| `manuscript.md` | 完整原稿（含 YAML metadata） |
| `epub-style.css` | EPUB 樣式（保守控制版面） |
| `cover.jpg` | 封面 1600×2560 |
| `release/` | 上架用 EPUB |
| `google-play-books-listing.md` | 上架文案（短／中／長）與分類、關鍵字 |
| `author-bio.md` | 作者簡介 |
| `google-play-preflight-report.md` | EPUBCheck 與上架前檢查報告 |
| `CLOSURE.md` | 結案紀錄與下一版改進清單 |

## 重新建置

需要 [pandoc](https://pandoc.org/) 與 [EPUBCheck](https://github.com/w3c/epubcheck)：

```bash
pandoc manuscript.md -o release/claude-code-5day-guide-v1.0-googleplay.epub \
  --css epub-style.css --epub-cover-image cover.jpg \
  --toc --toc-depth 1 --split-level 1
java -jar epubcheck.jar release/claude-code-5day-guide-v1.0-googleplay.epub
```

## 授權

© 2026 楊政憲. All rights reserved. Claude 與 Claude Code 為 Anthropic 的產品與商標，本書為作者獨立撰寫，與 Anthropic 無隸屬關係。

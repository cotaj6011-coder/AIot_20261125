# A2Z IEEE 論文草稿處理紀錄

## 專案目的

依據 [A2Z outline example.pdf](A2Z%20outline%20example.pdf)、Notion 中的 ICEIB 2027 投稿資訊，以及原 DIC3 專案資料，建立一份獨立的 A2Z IEEE 論文草稿。原始論文保留在 `main.tex`，新稿另存為 `main_a2z.tex`；兩者不可混為同一版本。

新稿標題：**Evidence-Aware Arrival-Time Parking Recommendations for New Taipei Roadside Parking**

## 使用資料與依據

- A2Z 寫作架構：`A2Z outline example.pdf`
- 投稿資訊：Notion「AIoT-DA L16 打造 AGENT (目標/系統架構PDAC)+OVERLEAF」頁面
- DIC3 專案來源：[AIot_20261111_DIC-ProjectRefactor](https://github.com/cotaj6011-coder/AIot_20261111_DIC-ProjectRefactor)，並以固定版本的 [DESIGN.md](https://github.com/cotaj6011-coder/AIot_20261111_DIC-ProjectRefactor/blob/c394e14781549d7d587bae8a99f0c02b7d67e1e2/DESIGN.md) 作為專案數據與流程敘述來源。
- 文獻資料：既有 `references.bib` 保持不變；A2Z 專用的 DIC3 來源引用放在 `references_a2z.bib`。

## 處理流程

1. 閱讀 A2Z 範例，整理預期的章節內容：Abstract A–F、Introduction G–L、Related Work M–O（含 SWOT）、Proposed Scheme PA–PM、Simulation Q–V、Conclusion W–Z。
2. 閱讀 Notion 投稿資訊。記錄 ICEIB 2027 預計於 2027 年 4 月 23–25 日舉行；全文頁數為 4–8 頁，摘要截止日為 2027 年 3 月 1 日，全文截止日為 2027 年 4 月 20 日。Notion 提及 IEEE 或 Engineering Proceedings 出版軌道。
3. 閱讀 DIC3 專案材料，區分新北市預測研究與台中市資訊查詢流程；不把資訊型代理描述成預測服務，也不把尚未執行的測試寫成結果。專案文件引用固定在 commit `c394e14781549d7d587bae8a99f0c02b7d67e1e2`。
4. 建立獨立的 `main_a2z.tex`，採 IEEEtran conference、letter paper、10 pt、pdfLaTeX 格式；A2Z 專用來源以 `references_a2z.bib` 引用，保留 `main.tex` 與共用的 `references.bib`。
5. 在 Overleaf 將 `main_a2z.tex` 設為主文件並編譯，確認 PDF 預覽為新稿而非原稿。
6. 審查論述、數據來源、公式邊界條件、A2Z 對照及編譯 log；本 README 記錄目前尚未完成的投稿前事項。

## 研究證據狀態

稿件提到的 New Taipei Phase 2 比較值是專案文件中的**來源報告值**，不是本稿重新執行或獨立驗證的結果：

| 模型 | MAE（spaces） | 狀態 |
| --- | ---: | --- |
| Persistence | 0.326757 | 專案文件報告，未重現 |
| Random Forest | 0.402669 | 專案文件報告，未重現 |
| HistGradientBoosting | 0.537539 | 專案文件報告，未重現 |

來源材料另報告 9,178,935 筆共同測試觀察值、4,966 與 5,047 個跨越名義切分邊界的目標時間戳、54.26% 有效觀察網格率，以及 +30／+60 分鐘目標的 85.35%／80.75% no-change 比例。以上數值尚未由本稿重算；`main_a2z.tex` 現在引用固定 commit 的 `DESIGN.md`，但這不等於重新執行或驗證 Phase 2 實驗。

SFpark 的搜尋時間變化僅作為外部研究動機，不是本研究代理的成果，也不是新北市的預測基準。

## 編譯與格式檢查

- 編譯位置：Overleaf 專案；主文件設定為 `main_a2z.tex`。
- 編譯結果：成功，PDF 共 4 頁，符合 Notion 所列 4–8 頁範圍。
- Overleaf log：0 errors、0 warnings；修正 validity 方程式換行後，已無 overfull hbox。仍有 underfull hbox/vbox typesetting 提示，需在最終 PDF 做視覺檢查。
- 基本格式：IEEEtran conference、letter paper、10 pt、IEEE keywords 與 IEEEtran bibliography。
- 範本限制：Notion 說明目前未能確認 ICEIB 專屬 IEEE LaTeX 範本；標準 IEEEtran 的編譯成功不等於主辦方已核可格式。正式投稿前應確認出版軌道、官方範本與最新作者規範。

## 投稿前待辦

- [x] 以固定 commit 的 DIC3 `DESIGN.md` 建立獨立 BibTeX 來源，並在稿件相關段落引用；專案報告數值仍未重算。
- [ ] 決定全文投稿是否必須提供已完成的實驗結果。目前 H1–H3、arrival-time Top-3 與故障注入評估都仍是計畫；若投稿軌道要求完整研究論文，需執行並報告結果。
- [x] 修正 freshness 條件為 `0 <= t - t_s <= tau`，拒絕未來時間戳。
- [x] 定義 `Q_s` 為正規化 freshness score，並定義 `D_max = 0` 且候選距離為 0 時的距離分數。
- [x] 將摘要內容依 A–F 的動機、挑戰、解方、方法、實驗計畫與目前發現順序重排；維持 IEEE 摘要單段呈現。
- [x] 拆分 validity 方程式以修正 overfull hbox，並重新編譯確認。
- [ ] 向 ICEIB 2027 主辦方確認 IEEE 或 Engineering Proceedings 軌道、官方模板、頁數與截止日期的最新版本。

## 檔案與版本狀態

- `main.tex`：原始論文，保留未修改。
- `main_a2z.tex`：獨立 A2Z 草稿；目前已上傳至 Overleaf 並成功編譯。
- `references.bib`：原有共用書目檔，未修改。
- `references_a2z.bib`：A2Z 專用書目檔，包含固定版本的 DIC3 `DESIGN.md` 引用。
- `README.md`：本處理流程與投稿前檢查紀錄。
- A2Z 稿與專用書目已更新至 Overleaf 並重新編譯；本次 GitHub 推送包含 `main_a2z.tex`、`references_a2z.bib` 與本紀錄。原始 `main.tex` 與 `references.bib` 未修改。

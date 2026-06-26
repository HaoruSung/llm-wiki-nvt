# CAD Team LLM Wiki — 操作手冊 (Schema)

這是一個由 LLM 維護的知識庫（wiki），服務對象是 IC design 的 **CAD team**。
資料來源主要是 **EDA tool guide（原廠文件）** 與 **user guide（內部使用指南）**。

本檔（CLAUDE.md）是這個 wiki 的「操作說明書」。你（LLM）每次 ingest 新文件、
回答問題、或維護 wiki 時，都必須遵循這裡定義的結構、慣例與工作流。
人類負責策展與校正；繁瑣的記帳（建頁、更新交叉引用、消除矛盾）由你負責。

---

## 0. 核心原則（每次動作前先記住）

1. **絕不把整本 wiki 讀進 context。** 你要像在大型 codebase 裡找東西一樣，
   先讀 `index.md`，再用 grep / glob 定位，只讀「命中的那幾頁」。
   （唯一例外是 Lint，那時才會大範圍掃描。）
2. **source 頁只增不改；tool / concept / command / procedure / issue 頁跨來源累積。**
   知識複利就發生在「反覆回來更新同一頁」這件事上。
3. **每次 ingest 都要更新 `index.md` 與 `log.md`。** 沒更新索引的頁面等於不存在。
4. **保留出處。** 任何一條 wiki 裡的事實，都要能追回是哪一份 source、哪個 tool 版本。
5. **不確定就標記，不要臆造。** EDA 行為高度依賴 tool 版本與 PDK；寧可標 `TODO` 或
   `⚠️ 未確認`，也不要編造 command 選項或數值。

---

## 1. 目錄結構

```
cad-wiki/
├── CLAUDE.md          # 本檔：操作手冊（schema）
├── index.md           # 目錄：所有頁面的 catalog（內容導向）
├── log.md             # 日誌：ingest / query / lint 的 append-only 紀錄（時間導向）
├── raw/               # 原始文件（PDF、html、txt…），不可變，使用者放入
│   └── assets/        # 從文件抽出的圖片
├── source/            # 每份 raw 文件一頁摘要（只增不改）
├── tool/              # EDA 工具頁（entity）
├── concept/           # 方法 / 流程 / 理論概念頁
├── command/           # 指令 / 選項 reference
├── procedure/         # how-to / flow 操作步驟（多半來自 user guide）
└── issue/             # 錯誤訊息 / 已知問題 / 排錯 / FAQ
```

---

## 2. 頁面類型（page types）

頁面是按「**扮演的角色**」分類，不是按主題分類。

| 類型 | 放什麼 | 與來源的關係 | 命名（kebab-case，wiki root 相對） |
|---|---|---|---|
| `source/`    | 一份原始文件的摘要 | **1 份文件 = 1 頁，只增不改** | `source/<date>-<doc-slug>.md` |
| `tool/`      | 一個 EDA 工具 | 跨來源累積 | `tool/<vendor>-<tool>.md` |
| `concept/`   | 方法 / 流程階段 / 理論 | 跨來源累積 | `concept/<slug>.md` |
| `command/`   | 一條指令或重要選項 | 跨來源累積 | `command/<tool>-<command>.md` |
| `procedure/` | 一個 how-to / flow | 跨來源累積 | `procedure/<slug>.md` |
| `issue/`     | 一個錯誤訊息 / 已知問題 | 跨來源 + query 回填 | `issue/<tool>-<short-slug>.md` |

### 分類判斷規則（ingest 時用來決定要長哪種頁）

**每型的「一句定義 + 判別問句」：**

| 類型 | 一句定義 | 判別問句 |
|---|---|---|
| `source/`    | 一份具體原始文件 | 是「一份文件」嗎？ |
| `tool/`      | 可被啟動、能掛上「廠商+版本+license」的軟體產品或 instrument（專有名詞） | 我能 invoke 它、它有版本與 license 嗎？ |
| `concept/`   | 一種「做事的方法 / flow 階段 / 理論」，**不是**能啟動的產品 | 它是「一種做法/想法」而非產品嗎？ |
| `command/`   | 能在 shell 執行的一條指令或選項 | 我能把它打進命令列執行嗎？ |
| `procedure/` | 達成某目標的有序步驟（how-to / flow） | 它是「照著做就能完成 X」嗎？ |
| `issue/`     | 錯誤訊息 / 症狀 / FAQ | 它是「遇到問題要排除」嗎？ |

**決策流程（每抽出一個項目，由具體到一般依序判斷）：**

```
是整份文件嗎？             → source
是可啟動的具名產品/IP 嗎？  → tool
是可執行的指令/選項嗎？     → command（見下方 granularity 規則）
是達成目標的有序步驟嗎？    → procedure
是錯誤/症狀/FAQ 嗎？       → issue
以上皆非（方法/概念/格式）  → concept
```

**tool vs concept（最常混淆，含 tie-breaker）：**
能掛上「廠商+版本+license」、可被 invoke 的 → **tool**；「一種做法/階段/理論」→ **concept**。
**同一件事既是產品又是方法時，拆成兩頁、互相連結**（產品歸 tool、方法歸 concept）。
- 例：`ATPG` 是 concept（方法）；`Tessent FastScan` 是 tool（做 ATPG 的產品）。

**command granularity（何時獨立成頁 vs 併進 tool 頁）：**
- **獨立成頁**，符合任一即可：①常用/常被問、②有非平凡的選項或陷阱（值得放選項表+範例）、③被 ≥2 個 procedure 或其他頁引用。
- **只當 tool 頁的一行 bullet**：用法單一、無重要選項、很少用。
- 命名一律 tool 前綴（`command/<tool>-<cmd>`）——同名指令在不同工具/版本行為可能不同。

**資料物件 / 檔案格式 / 資料庫（artifact，如 TSDB、SDC、LEF/DEF、`.lib`、STIL、test procedure file…）：**
這類是 flow 的「**產物**」，不是 concept。**目前先歸 `concept/`，但一律加 `#kind/format`（檔案格式）或 `#kind/infra`（資料庫/目錄結構）tag。**
- 升級門檻：當這類頁累積 **≥5 個且常被獨立查詢**時，再用 lint 拆出專屬 `artifact/` 類型（避免過早建類型）。

**反重複（一個事實，一個正本）：**
一個概念常同時觸發多種頁——這是正常的，不是重複。但**標準內容只放在「最具體的那一頁」，其他頁用連結指過去、不複製**，避免改一處要改多處。
> 例：一段「如何用 PrimeTime 跑 STA signoff」會更新 `tool/synopsys-primetime`、
> `concept/static-timing-analysis`、新建 `procedure/run-sta-signoff` 與數個 `command/primetime-*`；
> 其中各 command 的**完整選項表只放在對應 command 頁**，其他頁只連結。

---

## 3. 命名與連結慣例

- **檔名**：全小寫、kebab-case。指令名保留原本的底線，方便 grep 命中真實指令：
  `command/primetime-report_timing.md`、`tool/synopsys-primetime.md`、
  `concept/clock-tree-synthesis.md`、`issue/calibre-lvs-property-mismatch.md`。
- **交叉連結**：用 wiki-link，路徑相對 wiki root，**含類型前綴**：
  `[[concept/static-timing-analysis]]`、`[[tool/cadence-innovus]]`。
  建頁或更新頁時，凡提到別頁主題就加連結——這是讓 wiki 變成「圖」的關鍵。
- **Tags**（每頁頂部，方便跨切面查詢）：
  - flow 階段：`#stage/synthesis #stage/place #stage/cts #stage/route #stage/sta #stage/pv #stage/extraction #stage/power`
  - 廠商：`#vendor/synopsys #vendor/cadence #vendor/siemens #vendor/ansys`
  - 種類（選用，標記 artifact 候選）：`#kind/format`（檔案格式）`#kind/infra`（資料庫/目錄結構）— 見 §2 artifact 處理
  - 狀態：`#status/verified #status/unverified #status/superseded`

---

## 4. Tool 版本處理（本領域特別重要）

EDA 行為高度綁定工具版本與 PDK，務必遵守：

- **每個 source 頁都要記錄它對應的 tool 版本與（若有）PDK / 製程節點。**
- tool / command / issue 頁的事實，盡量在行尾標註版本來源，例如：
  `set_max_transition 的預設行為（PT 2024.03，見 [[source/...]]）`。
- 新文件推翻舊行為時：**不要刪除舊內容**，把舊行為標 `#status/superseded` 並註明被哪一版取代，
  在 log.md 記一筆。讓「版本演進」本身可被查詢。

---

## 5. 頁面模板

### 5.1 source/

```markdown
# <文件標題>
#status/verified
- **Type**: tool guide | user guide
- **Vendor / 來源**: Synopsys / Cadence / 內部 CAD team / ...
- **Tool & Version**: PrimeTime 2024.03 (若適用)
- **PDK / 製程**: (若適用)
- **Raw file**: [[raw/<檔名>]]
- **Ingested**: YYYY-MM-DD

## 重點摘要
- (3~10 條 bullet，這份文件的核心內容)

## 本次 ingest 牽動的頁面
- 新建：[[command/...]]、[[issue/...]]
- 更新：[[tool/...]]、[[concept/...]]
```

### 5.2 tool/

```markdown
# <Tool 全名>
#vendor/<vendor> #stage/<stage> #status/verified
- **Vendor**: 
- **Category**: synthesis | P&R | STA | PV(DRC/LVS) | extraction | simulation | power
- **Latest known version**: 
- **License feature**: 
- **所屬 flow 階段**: [[concept/...]]

## 用途 / 在 flow 中的角色

## 常用 commands
- [[command/...]] — 一行說明

## 常見問題 / 排錯
- [[issue/...]] — 一行說明

## 相關 procedure
- [[procedure/...]]

## 出處
- [[source/...]]
```

### 5.3 concept/

```markdown
# <概念名稱>
#stage/<stage> #status/verified
- **一句話定義**: 

## 說明

## 相關工具
- [[tool/...]]

## 相關指令 / 流程
- [[command/...]]、[[procedure/...]]

## 出處
- [[source/...]]
```

### 5.4 command/

```markdown
# <command 名稱>
#vendor/<vendor> #status/verified
- **所屬工具**: [[tool/...]]
- **語法**: `command -opt <value>`

## 用途

## 重要選項
| 選項 | 說明 | 預設 | 版本備註 |
|---|---|---|---|

## 範例
```tcl
# 可直接複用的範例
```

## 注意事項 / 陷阱

## 出處
- [[source/...]]
```

### 5.5 procedure/

```markdown
# <要完成的事>
#stage/<stage> #status/verified
- **目標**: 
- **前置需求**: license、PDK、環境變數、輸入檔…
- **相關工具**: [[tool/...]]

## 步驟
1. 
2. 

## 驗證方式 / 預期輸出

## 常見踩雷
- [[issue/...]]

## 出處
- [[source/...]]
```

### 5.6 issue/

```markdown
# <簡短問題描述>
#vendor/<vendor> #status/verified
- **所屬工具**: [[tool/...]]
- **錯誤訊息（原文，供 grep 命中）**:
  ```
  Error: <貼上完整錯誤訊息>
  ```

## 症狀

## 原因

## 解法 / workaround

## 相關
- [[procedure/...]]、[[command/...]]

## 出處
- [[source/...]] 或 (query 回填，YYYY-MM-DD)
```

---

## 6. 工作流：Ingest（匯入新文件）

當使用者把新文件放進 `raw/` 並要求 ingest 時：

1. **讀** `raw/` 中的新文件。若含關鍵圖片，存到 `raw/assets/` 並在相關頁引用。
2. **抽取**：列出文件中的工具、概念、指令、操作步驟、錯誤訊息。
   同時記下這份文件對應的 **tool 版本 / PDK**。
3. **定位既有頁**：對每個抽出的名字，**先查 `index.md`，再 `grep` 全 wiki**。
   - 已存在 → 局部更新該頁（補新資訊、調和矛盾、加版本備註、加交叉連結）。
   - 不存在 → 依判斷規則（§2）新建對應類型的頁，套用 §5 模板。
4. **寫 source 摘要頁**（§5.1），列出本次牽動了哪些頁。
5. **更新 `index.md`**：新增 / 修改條目（見 §9 格式）。
6. **追加 `log.md`** 一筆（見 §10 格式）。
7. **回報**：用 1 段話跟使用者說「讀到什麼、建/改了哪些頁、有哪些不確定處」。

> 一份文件通常牽動 **10–15 頁**。可批次 ingest 多份，但批次時更要嚴格更新 index/log。
> **只讀「命中的頁」，不要重讀整本 wiki。**

---

## 7. 工作流：Query（回答問題）

1. **讀 `index.md`** 了解有哪些頁。
2. **grep / glob** 用問題中的關鍵字（工具名、指令名、錯誤訊息、flow 階段）定位。
3. **只讀命中的 3~10 頁**，綜合出答案，**附上出處連結**（引用到頁與 source）。
4. 若某條資訊在 wiki 中缺漏或過時，**明講「wiki 沒有 / 不確定」**，必要時建議去查原廠文件或開 web search，
   不要臆造。
5. **回填**：若這次答案有重用價值（尤其是排錯類），把它整理成 `issue/` 或 `procedure/` 新頁，
   更新 index/log。

---

## 8. 工作流：Lint（定期健檢）

定期（或使用者要求時）大範圍掃描，找出並修正：

- **矛盾**：兩頁對同一行為說法不一 → 多半是版本差異，補版本備註或標 superseded。
- **過時**：被新版工具 / 新 source 推翻的舊主張 → 標 `#status/superseded`。
- **孤立頁**：沒有任何 inbound 連結的頁 → 補交叉連結或併入相關頁。
- **缺頁**：被反覆提到卻沒有獨立頁的工具 / 概念 / 指令 → 補建。
- **缺連結**：頁中提到別的主題卻沒連 → 補上 wiki-link。
- **未驗證**：`#status/unverified` 或 `TODO` 累積太多 → 列清單請人類確認。
- **版本健康度**：列出沒有標註 tool 版本的事實，提醒補齊。

完成後在 `log.md` 記一筆 lint 摘要（改了什麼、留下哪些待辦）。

---

## 9. `index.md` 格式（內容導向的目錄）

依類型分區，每條：`連結 — 一行摘要 — (選用 metadata)`。範例：

```markdown
## Tools
- [[tool/synopsys-primetime]] — Signoff STA 工具 · #stage/sta
- [[tool/cadence-innovus]] — Place & Route · #stage/place #stage/route

## Concepts
- [[concept/static-timing-analysis]] — 靜態時序分析的原理與流程

## Commands
- [[command/primetime-report_timing]] — 輸出 timing path 報告

## Procedures
- [[procedure/run-sta-signoff]] — 跑一次 signoff STA 的完整步驟

## Issues
- [[issue/calibre-lvs-property-mismatch]] — LVS property mismatch 排錯

## Sources
- [[source/2026-06-25-primetime-user-guide]] — PrimeTime 2024.03 user guide
```

---

## 10. `log.md` 格式（append-only，可被 unix 工具解析）

每筆以可解析的標題開頭：`## [YYYY-MM-DD] <ingest|query|lint> | <標題>`

```markdown
## [2026-06-25] ingest | PrimeTime 2024.03 User Guide
- 來源：[[source/2026-06-25-primetime-user-guide]]（tool guide, PT 2024.03）
- 新建：[[tool/synopsys-primetime]]、[[concept/static-timing-analysis]]、
  [[command/primetime-report_timing]]、[[procedure/run-sta-signoff]]
- 更新：[[index.md]]
- 待確認：report_timing 的 -delay_type 在 2023.x 的預設值

## [2026-06-25] query | 如何降低 max transition violation
- 讀取：[[command/primetime-report_timing]]、[[concept/...]]
- 回填：[[issue/primetime-max-transition-violation]]
```

---

## 11. 機密性提醒

- 原廠 tool guide 多受 NDA 保護；內部 user guide 含公司流程。**此 wiki 視為機密**，
  不得外傳，不得貼到外部服務。
- 不確定某內容是否可記錄時，標記並詢問人類，不要自行外送或上網查證機密細節。

---

## 12. 這份手冊會持續演進

當你（LLM）行為不一致、或人類給了新慣例時，把該慣例**結晶回本檔**（新增一條規則 / 模板），
並在 `log.md` 記一筆 `lint | schema update`。這份 CLAUDE.md 本身就是會複利成長的「規則庫」。

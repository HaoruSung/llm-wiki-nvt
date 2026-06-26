# TSDB (Tessent Shell Database)
#stage/dft #kind/infra #status/verified
- **一句話定義**: Tessent Shell 在 flow 中產生的所有目錄與檔案的中央資料庫，讓各 Tessent 工具能取用當前任務所需資料。
- **分類備註**: 屬 artifact（資料庫）候選；目前暫歸 `concept/` + `#kind/infra`，達門檻後再拆 `artifact/`（見 [[CLAUDE.md]] §2）。

## 說明
TSDB 是 flow 自動化的中樞：無論是讀設計、跑 DRC、插入測試硬體、還是 ATPG 產 pattern，工具都從 TSDB 存取所需資料。詳見手冊「TSDB Data Flow for the Tessent Shell Flow」章節（後續可再 ingest 深掘）。

## 相關工具
- [[tool/siemens-tessent-shell]]

## 相關概念
- [[concept/tessent-contexts-and-system-modes]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]

# Log — CAD Team Wiki 日誌

> Append-only。每筆以 `## [YYYY-MM-DD] <ingest|query|lint> | <標題>` 開頭。
> 格式見 [[CLAUDE.md]] §10。

## [2026-06-25] lint | wiki initialized
- 建立 schema（CLAUDE.md）、index.md、log.md 與目錄骨架。
- 尚未 ingest 任何 source。

## [2026-06-25] ingest | Tessent Shell User's Manual v2021.3
- 來源：[[source/2026-06-25-tessent-shell-user-manual]]（tool guide, Siemens, Tessent Shell 2021.3, ⚠️NDA）
- raw：[[raw/tshell_user.pdf]]（101 頁；本次為示範，重點抽取 Ch.1–2 + Appendix A，未逐頁全讀）
- 新建：[[tool/siemens-tessent-shell]]、[[concept/dft-design-for-test]]、[[concept/tessent-contexts-and-system-modes]]、[[concept/tsdb]]、[[command/tessent-set_context]]、[[procedure/invoke-tessent-shell-and-set-context]]、[[issue/tessent-tcl-dollar-sign-in-pathname]]
- 更新：[[index.md]]
- 待深掘（後續 ingest）：SSN、TSDB Data Flow、Hierarchical DFT、Test Procedure File、Tessent Visualizer、Automotive Workflow
- 待確認：各 context 對應的精確 license feature 名稱（需查 Reference Manual）

## [2026-06-25] lint | schema update — 細化類型判斷規則
- CLAUDE.md §2：新增每型「定義+判別問句」、決策流程、tool↔concept tie-breaker、
  command granularity 規則、artifact（資料物件/格式）暫歸 concept + `#kind/` tag 並設升級門檻（≥5 頁）、
  反重複「一個事實一個正本」規則。
- CLAUDE.md §3：tag 清單新增 `#kind/format` / `#kind/infra`。
- 套用：[[concept/tsdb]] 補上 `#kind/infra` 並加分類備註（artifact 候選）。

## [2026-06-25] ingest | Tessent Shell Manual — Chapter 3 (Design Introspection and Editing)
- 來源：[[source/2026-06-25-tessent-shell-user-manual]]（同份文件，行 1672–4050；含 Ch.2 data model 補強）
- 新建 12 頁：
  - concept：[[concept/design-introspection]]、[[concept/collections]]、[[concept/object-attributes]]、[[concept/design-editing]]、[[concept/simulation-contexts]]、[[concept/design-data-models]]、[[concept/test-procedure-file]]（#kind/format, stub）
  - command：[[command/tessent-get_instances]]、[[command/tessent-get_attribute_value_list]]、[[command/tessent-read_verilog]]、[[command/tessent-create_flat_model]]
  - issue：[[issue/tessent-design-editing-unavailable-under-fastscan-scan-license]]
- 更新 4 頁：[[tool/siemens-tessent-shell]]（接上新概念/指令）、[[concept/tessent-contexts-and-system-modes]]（補 analysis mode）、[[source/2026-06-25-tessent-shell-user-manual]]（章節進度）、[[index.md]]
- granularity 決策：Table 3-2/3-3/3-6 共 ~30 條指令，**僅 4 條獨立成頁**（有選項/陷阱/被多處引用），其餘列為概念頁 bullet，避免碎片化。
- artifact 候選累積：tsdb(#kind/infra) + test-procedure-file(#kind/format) = 2，**未達 ≥5 門檻**，暫不建 `artifact/`。
- 待確認：`get_instances` 等完整選項（需 Reference Manual）；ICL data model / Automatic Design Mapping 僅淺記，待深掘。

## [2026-06-25] ingest | Tessent Shell Manual — Chapter 4 (DFT Architecture Guidelines for Hierarchical Designs)
- 來源：[[source/2026-06-25-tessent-shell-user-manual]]（同份文件，行 4051–4678）
- 本章為**純方法論**：concept 大量新增、**無新 command / issue**（命令 defer 至 Tessent Scan and ATPG 手冊）。
- 新建 9 頁（concept）：[[concept/hierarchical-dft]]、[[concept/wrapped-cores-and-wrapper-cells]]、[[concept/internal-external-mode]]、[[concept/on-chip-clock-controller]]、[[concept/graybox-model]]、[[concept/pattern-retargeting]]、[[concept/test-access-mechanism]]、[[concept/hierarchical-dft-planning]]、[[concept/edt]]（#status/unverified, 多處引用）
- 更新 4 頁（複利）：[[concept/dft-design-for-test]]（新增 hierarchical 方法論區塊）、[[concept/tessent-contexts-and-system-modes]]（`dft -edt`、`patterns -scan_retargeting`、design level 連到新概念頁）、[[concept/design-data-models]]（連 graybox）、[[tool/siemens-tessent-shell]]
- 更新比例高於 Ch.3：既有的 context bullet 從「純文字」變成「連到概念頁」，dft 頂層概念頁長出方法論分支。
- 待確認/深掘：two-pass hierarchical insertion flow（Ch.5）、OCC parent/child 細節、TAM 與 floorplan 互動。

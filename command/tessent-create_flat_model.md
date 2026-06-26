# create_flat_model
#vendor/siemens #status/verified
- **所屬工具**: [[tool/siemens-tessent-shell]]
- **語法**: `create_flat_model [...]`

## 用途
明確建立 flat design data model（進入 analysis mode 時也會自動建立）。flat model 由相連 gate 組成，供 gate_pin 級的 introspection 與模擬。

## 注意事項
- flat model 的 `gate_pin` ID（gateID.pinIndex）**跨版本 / 跨 invocation 不穩定，勿 hard-code**。
- 保留 flat model 中的 hierarchical pin：`set_attribute_options -preserve_boundary_in_flat_model`。

## 相關
- [[concept/design-data-models]]、[[concept/simulation-contexts]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.2–3）

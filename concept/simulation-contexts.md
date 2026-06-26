# Simulation Contexts
#stage/dft #status/verified
- **一句話定義**: 一組預定義狀態，讓你對 flat model 的 gate_pin 取得對應的模擬值，用於設計分析與 introspection。

## 說明
- 四個預定義 context：`stable_after_setup`、`stable_load_unload`、`stable_shift`、`stable_capture`。
- 模擬值四種：0 / 1 / X / Z。
- **前置條件**：須在 **analysis system mode**（見 [[concept/tessent-contexts-and-system-modes]]）、操作 flat model、並讀入 [[concept/test-procedure-file]]（若有）。
- 設定後可用 introspection 指令查 gate_pin 模擬值，或在 Tessent Visualizer Flat Schematic 看值。

## 主要指令
- 設定：`set_current_simulation_context <ctx>`（如 `stable_shift`）
- 查 / 追蹤：`get_simulation_value_list`、`trace_flat_model`、`report_simulation_contexts`、`get_current_simulation_context`、`get_simulation_context_list`
- 施力 / 脈衝：`simulate_forces`、`simulate_clock_pulses`、`set_gate_report`

## 相關
- [[concept/design-data-models]]、[[concept/design-introspection]]、[[concept/test-procedure-file]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.3）

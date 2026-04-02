# 01｜Harness Day1 基线包（AI PM 可直接执行）

目标：在不改系统策略前，先拿到可对比的 baseline 数据。

## 一、样本设计（30 条中文 query）

建议分 3 类，每类 10 条：

1. 信息型任务（总结、解释、对比）
2. 执行型任务（读写文件、命令执行、修复）
3. 治理型任务（权限、风险、边界条件）

每条 query 都要带：
- 任务目标
- 期望输出格式
- 成功判定标准（最少一句）

## 二、记录字段（最小可用）

- query_id
- query_text
- task_type
- expected_output
- finished_in_one_turn（Y/N）
- turn_count
- tool_calls
- input_tokens
- output_tokens
- total_cost_est
- blocked_by_permission（Y/N）
- error_type
- final_status（success/partial/fail）
- notes

## 三、今天要交付的三个产物

1. `day1-baseline-template.csv` 填满 30 条样本。
2. 计算基线：一次完成率、平均回合数、平均成本、误拦截率。
3. 产出 1 页结论：当前主要失败类型 Top3。

## 四、通过标准（Day1）

- 样本可回放（下周还能用同一批重跑）
- 指标口径固定（不临时改定义）
- 失败归因可落到系统层（Prompt/Route/Permission/Runtime/Cost）


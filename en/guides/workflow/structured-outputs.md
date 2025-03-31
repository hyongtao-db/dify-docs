## Overview

Dify’s structured outputs ensures LLMs return data in predictable JSON formats, making the output easier to process and integrate into applications.

## Benefits

- Consistent data formatting
- Direct integration with databases and APIs
- Simplified data validation through JSON Schema

## Methods

在 Dify 的操作界面中，可以通过以下两种方式实现结构化输出：

-   **方式一：直接定义工具参数**
-   **方式二：使用 LLM 节点中的 **JSON Schema 编辑器**

### 方式一：直接定义工具参数

See **[Tool](https://docs.dify.ai/plugins/schema-definition/tool) > Data Structures > Return Variable Definitions**。

### 方式二：使用 LLM 节点中的 JSON Schema 编辑器

See **[LLM](https://docs.dify.ai/guides/workflow/node/llm) > Advanced Features > Structured Outputs**。

## 异常处理方案

**异常情况**

在使用 JSON Schema 编辑器进行结构化输出时，可能会遇到以下限制和异常情况：

-   **模型能力限制**：部分 LLM（尤其是 70B 以下的模型或 GPT-3.5 Turbo 级别模型）在指令遵循性上较弱，可能导致 JSON Schema 解析失败。
-   **格式兼容性**：部分 LLM 仅支持 **JSON mode** 而非 **JSON Schema**，导致严格的 Schema 解析失败。
-   **错误信息**：出现错误 `Failed to parse structured output: output is not a valid json str`。此类错误主要源于模型生成 JSON 失败。

**推荐处理方案**

1.  **优先使用支持 JSON Schema 的模型**。推荐列表如下：
    - Gemini 2.0 Flash/Flash-Lite
    - Gemini 1.5 Flash 8B (versions 0827/0924)
    - Gemini-1.5 pro
    - GPT-4o and GPT-4o-mini
    - o1-mini/o3-mini series

2.  **适当调整系统提示词以增强指令遵循性，尽可能确保 LLM 输出符合 Schema 规范**。假如 JSON Schema 设计用于结构化数学公式的输入与输出，而系统提示词却要求模型进行法律条文解析，这种不匹配可能会导致模型无法正确理解任务，影响生成结果的准确性。

3.  **配置异常处理策略**。你可以在解析失败时考虑采取以下措施：
    1.  **配置失败时重试**：在节点内开启 **失败时重试** 功能并配置最大重试次数与重试间隔，以减少解析错误的影响。
    2.  **配置异常分支**：在节点内的 **异常处理** 中配置 **失败分支。**当节点发生异常时，将自动执行失败分支。

详情请参阅[异常处理](https://docs.dify.ai/zh-hans/guides/workflow/error-handling)。
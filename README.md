# RIM AGENT — 环世界开发助手

> 专为 [RimWorld](https://rimworldgame.com/) Mod 开发与调试设计的智能 Agent。

---

## 简介

RIM AGENT 是一个面向 RimWorld 的分析师与开发助手，能够深入分析 Mod 内容、源码、XML Def、程序集以及游戏运行时行为，帮助开发者快速定位问题、理解 Mod 结构并评估兼容性。

---

## 核心能力

| 模式 | 说明 |
|------|------|
| **Analyze（分析）** | 解析 Mod 的文件结构、XML Def、C# 代码、Harmony Patch 及游戏逻辑 |
| **Debug（调试）** | 调查错误、异常、兼容性冲突及非预期行为，定位根因并提供修复方向 |

---

## 使用方式

启动 Agent 时，通过 `argument-hint` 描述以下内容：

- 工作区路径或目标 Mod
- 分析目标（如特定文件、类、方法、XML Def）
- 遇到的问题或需要调试的运行现象
- 期望的分析深度或范围

### 示例

```
分析工作区 ./Mods/MyMod，重点关注 Building_Door 的 Harmony Patch 兼容性
```

```
Debug：游戏启动时抛出 NullReferenceException，涉及 Verse.Thing 的初始化流程
```

---

## 分析维度

### 1. 内容分析（Content Analysis）
识别 Mod 中新增或修改的游戏内容与玩法机制。

### 2. 结构分析（Structure Analysis）
梳理文件组织方式，定位关键定义文件与资源引用关系。

### 3. 逻辑分析（Logic Analysis）
深入 XML Def、C# 源码、Harmony Patches 的实现细节与运行时调用链路。

### 4. 兼容性分析（Compatibility Analysis）
评估依赖关系、Mod 集成方式，识别潜在冲突与加载顺序问题。

> 分析结果将明确区分 **事实**、**推断** 与 **未知项**，并根据可用证据动态调整深度。

---

## 工具链

### rimworld-code-rag MCP
用于 RimWorld 代码的智能检索与符号查询：

| 方法 | 用途 |
|------|------|
| `rough_search` | 模糊搜索 Def 或代码符号 |
| `get_uses` | 查询 C# 符号的调用关系 |
| `get_used_by` | 查询 XML Def 的引用关系 |
| `get_item` | 获取符号定义详情 |

**符号命名规范：**
- C# 类型：`Namespace.TypeName`（如 `RimWorld.Building_Door`、`Verse.Thing`）
- XML Def：`xml:DefName`（如 `xml:Gun_Revolver`、`xml:Door`）

### ILSpy CMD
当源码不可用时，通过反编译分析程序集：

```bash
ilspycmd [options] <assembly_file>
```

支持 `.dll`、`.exe` 及 `.nupkg`（配合 `--dump-package`）。

---

## 输出规范

- 直接返回分析/调试报告，不附加额外解释
- 包含证据引用、结论推导及不确定性说明
- 区分事实、假设与待验证项

---

## 适用场景

- ✅ Mod 代码审查与结构梳理
- ✅ XML Def 冲突与覆盖分析
- ✅ Harmony Patch 行为追踪
- ✅ 运行时异常与兼容性故障排查
- ✅ 跨 Mod 依赖关系评估

---

## 注意事项

- 分析深度取决于提供的文件与日志证据的完整性
- 对于反编译代码，结论可能存在不确定性，将明确标注
- 建议配合具体错误日志、StackTrace 或最小复现案例使用 Debug 模式

---

*为环世界开发者提供精准、深入的代码级洞察。*

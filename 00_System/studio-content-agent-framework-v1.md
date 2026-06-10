# studio-content 知识库架构审计与 Multi-Agent 接入框架 V1.0

> 目的：把 `studio-content` 从“资料库”升级为“可被 Multi-Agent 调用、检索、推理、生成内容的专业知识系统”。

---

## 0. 当前判断

这个仓库已经不是简单素材收集，它更像一个正在形成的 **全屋定制 / 木作内容操作系统**。

但它现在最大的问题是：

```text
资料很多
↓
结构初步存在
↓
但知识之间的关系还不够清楚
↓
Agent 能读取，却不一定能推理
```

所以接下来不是继续堆资料，而是把资料整理成：

```text
实体
属性
关系
使用场景
风险
内容选题
Agent调用规则
```

---

## 1. 仓库目录扫描概览

| 一级目录/文件 | 文件数 | 建议知识库归属 |
|---|---:|---|
| CLAUDE.md | 1 | Agent Constitution |
| Daily | 1 | Session/Project Memory KB |
| README.md | 1 | Root System Map |
| _extracted | 27 | Course/Content Method KB |
| 专业知识库 | 1 | Knowledge Access Index |
| 倩倩的节奏.canvas | 1 | Unclassified / Review |
| 工商变更-木属艺科技.md | 1 | Unclassified / Review |
| 木作 | 1544 | Product/Material/Craft/Delivery/Operations KB |
| 案例 | 21 | Case KB |
| 案例仓库 | 8 | Case Template KB |
| 模板 | 2 | Template KB |
| 自媒体 | 90 | Content/Publishing KB |
| 运营策略 | 2 | Business/Publishing KB |
| 风格手册 | 7 | Content Standards KB |

---

## 2. 当前目录结构摘要

```text
- Daily/  (1 files)
  - 2026-06-03.md
- _extracted/  (27 files)
  - 001_认知准备篇：全面理解短视频和自媒体生态.txt
  - 002_认知准备篇：流量变现思维.txt
  - 003_认知准备篇：流量变现策略.txt
  - 004_认知准备篇：加餐极简AI课.txt
  - 005_方向篇：账号和人设的定位以及竞争优势(上).txt
  - 006_方向篇：账号和人设的定位以及竞争优势(中).txt
  - 007_方向篇：账号和人设的定位以及竞争优势(下).txt
  - 008_方向篇：常规爆款与原创工作流程.txt
  - 009_方向篇：创意选题的新角度.txt
  - 010_基本功篇：视频制作基本功.txt
  - 011_基本功篇：文字_语言基本功.txt
  - 012_基本功篇：镜头表现力基本功.txt
  - 013_基本功篇：空间的处理和调度.txt
  - 014_基本功篇：物品的视觉效果设计.txt
  - 015_基本功篇：大纲架构与材料组织思维.txt
  - 016_基本功篇：内容数据复盘以及运营规划.txt
  - 017_进阶篇：流量漏斗思维.txt
  - 018_进阶篇：信息效率思维.txt
  - 019_进阶篇：政治思维.txt
  - 020_进阶篇：结构的精细化处理(钩子).txt
  - 021_进阶篇：结构的精细化处理(骨架).txt
  - 022_进阶篇：结构的精细化处理(情绪刺点).txt
  - 023_进阶篇：情境化思维.txt
  - 024_进阶篇：故事性思维.txt
  - 025_进阶篇：用画面讲故事.txt
  - 026_进阶篇：导演风格构思.txt
  - 027_进阶篇：叙事美学「时间的语法(上)」.txt
- 专业知识库/  (1 files)
  - README.md
- 木作/  (1544 files)
  - 01_厨房基础/  (33 files)
    - 中西厨/  (1 files)
    - 基础装修/  (15 files)
    - 橱柜构成/  (2 files)
    - 水电管道/  (4 files)
    - 电器规划/  (11 files)
  - 02_材料体系/  (105 files)
    - 五金配件/  (50 files)
    - 台面材料/  (24 files)
    - 施工工艺/  (11 files)
    - 板材科普/  (17 files)
    - 柜体材料/  (3 files)
  - 03_功能设计/  (208 files)
    - 动线规划/  (10 files)
    - 尺寸与高度/  (90 files)
    - 收纳设计/  (104 files)
    - 灯光与卫生/  (4 files)
  - 04_五金配件/  (21 files)
    - 拉篮与收纳件/  (11 files)
    - 水盆与龙头/  (4 files)
    - 铰链与滑轨/  (6 files)
  - 04_产品系列/  (274 files)
    - 悬挂柜/  (117 files)
    - 特殊柜型（斜角柜/  (132 files)
    - 系统柜/  (22 files)
    - 门墙柜/  (3 files)
  - 05_厨房电器/  (45 files)
    - 其他电器/  (35 files)
    - 嵌入式电器/  (4 files)
    - 烟机灶具/  (6 files)
  - 06_工艺体系/  (386 files)
    - 五金配件/  (1 files)
    - 免拉手工艺/  (21 files)
    - 安装交付/  (2 files)
    - 收口工艺/  (3 files)
    - 收口工艺（海棠角/  (104 files)
    - 柜体工艺/  (140 files)
    - 标准柜工艺/  (5 files)
    - 特殊柜工艺/  (19 files)
    - 细节处理/  (3 files)
    - 细节处理（灯光/  (34 files)
    - 细节收口/  (16 files)
    - 门板工艺/  (3 files)
    - 门板工艺（一门到顶/  (35 files)
  - 07_测量与绘图/  (115 files)
    - 图纸规范/  (30 files)
    - 拍照存档/  (5 files)
    - 现场测量/  (80 files)
  - 08_安装交付/  (126 files)
    - 施工工序/  (78 files)
    - 水电交底/  (26 files)
    - 验收标准/  (22 files)
  - 09_供应链/  (38 files)
    - 成本与报价/  (13 files)
    - 材料选择与标准/  (25 files)
  - 10_工作室运营/  (191 files)
    - 差异化服务/  (61 files)
    - 常见问题与痛点/  (125 files)
    - 成本与报价/  (3 files)
    - 薪酬体系/  (2 files)
  - review_progress.json
  - 知识库_审查稿.md
- 案例/  (21 files)
  - 政立路/  (21 files)
    - 参考-AI生成版本/  (4 files)
    - 拍摄执行方案/  (5 files)
    - 数据复盘/  (2 files)
    - 短视频脚本/  (8 files)
    - 长视频脚本/  (1 files)
    - 案例基本信息.md
- 案例仓库/  (8 files)
  - 新案例模板/  (7 files)
    - 图片/  (3 files)
    - 01_基本信息.md
    - 02_木作内容.md
    - 03_图片资料.md
    - 04_故事点与补拍.md
  - README.md
- 模板/  (2 files)
  - space-explanation-model.md
  - 案例资料收集表.md
- 自媒体/  (90 files)
  - 01_生态认知/  (18 files)
    - 变现策略/  (2 files)
    - 流量变现思维/  (7 files)
    - 短视频生态/  (9 files)
  - 02_账号定位/  (13 files)
    - 人设设计/  (4 files)
    - 爆款与原创流程/  (3 files)
    - 竞争优势/  (4 files)
    - 账号定位/  (2 files)
  - 03_内容创意/  (10 files)
    - 内容架构与材料组织/  (3 files)
    - 创意选题/  (5 files)
    - 原创工作流/  (2 files)
  - 04_制作基本功/  (16 files)
    - 文案语言/  (4 files)
    - 空间调度与视觉效果/  (5 files)
    - 视频制作/  (4 files)
    - 镜头表现力/  (3 files)
  - 05_运营复盘/  (11 files)
    - 数据复盘/  (3 files)
    - 流量漏斗与信息效率/  (4 files)
    - 运营规划/  (4 files)
  - 06_爆款结构/  (16 files)
    - 情境化与故事性思维/  (5 files)
    - 情绪刺点/  (4 files)
    - 钩子与骨架/  (7 files)
  - 07_叙事美学/  (6 files)
    - 导演风格/  (1 files)
    - 时间语法与叙事节奏/  (3 files)
    - 用画面讲故事/  (2 files)
- 运营策略/  (2 files)
  - 投放入门-千帆与聚光.md
  - 数字转化三条路.md
- 风格手册/  (7 files)
  - 下单核对模板.md
  - 报价体系.md
  - 拍摄执行包样式模板.md
  - 拍摄执行标准模板.md
  - 案例输入模板.md
  - 短视频发布前QC清单.md
  - 账号主页设置.md
- CLAUDE.md
- README.md
- 倩倩的节奏.canvas
- 工商变更-木属艺科技.md
```

---

## 3. 建议拆分成 8 个 Agent 知识库

### 3.1 Product KB：产品 / 空间知识库

**来源目录：**

```text
木作/01_厨房基础
木作/03_功能设计
木作/04_产品系列
```

**解决问题：**

- 这个空间或柜体是什么？
- 它解决什么生活问题？
- 它由哪些结构组成？
- 它适合什么人群 / 场景？

**典型实体：**

```text
厨房
衣柜
玄关柜
餐边柜
阳台柜
电器高柜
冰箱高柜
```

**Agent用途：**

- 给用户解释一个空间系统
- 生成“柜子不是柜子，是系统”的内容
- 判断某个设计是否服务真实生活行为

---

### 3.2 Material KB：材料知识库

**来源目录：**

```text
木作/02_材料体系
```

**解决问题：**

- 材料是什么？
- 材料的性能是什么？
- 材料给人的感受是什么？
- 材料适合什么空间与人群？
- 材料有什么风险？

**典型实体：**

```text
颗粒板
多层板
密度板
石英石
岩板
不锈钢
玻璃
木皮
PET
烤漆
```

**需要补充的 Human-Environment 字段：**

```text
感官反馈：冷/暖/硬/软/轻/重/粗/滑
情绪影响：安全感/秩序感/疏离感/温暖感
适合人格：高掌控/高连接/高效率/低刺激需求
```

---

### 3.3 Craft KB：工艺知识库

**来源目录：**

```text
木作/06_工艺体系
```

**解决问题：**

- 工艺是什么？
- 它服务哪个结构？
- 它影响什么体验？
- 它解决什么风险？

**典型实体：**

```text
封边
收口
开槽
打孔
喷涂
铰链安装
拉手安装
组装
```

**Agent用途：**

- 专业校验
- 工艺科普
- 把“卖点”转成“行为结果”
- 判断内容脚本是否专业错误

---

### 3.4 Delivery KB：测量 / 安装 / 交付知识库

**来源目录：**

```text
木作/07_测量与绘图
木作/08_安装交付
```

**解决问题：**

- 现场怎么测？
- 图纸怎么核？
- 水电交底看什么？
- 安装风险在哪里？
- 验收标准是什么？

**Agent用途：**

- 生成施工交底清单
- 生成验收清单
- 生成“翻车原因”内容
- 帮用户判断责任边界

---

### 3.5 Supply & Ops KB：供应链 / 工作室运营知识库

**来源目录：**

```text
木作/09_供应链
木作/10_工作室运营
运营策略
```

**解决问题：**

- 供应链如何选择？
- 价格如何构成？
- 工作室如何服务客户？
- 谁设计、谁管理、谁安装、谁负责？

**Agent用途：**

- 支持“缝合怪木作中转站”
- 生成报价解释
- 生成责任划分说明
- 设计轻咨询产品

---

### 3.6 Case KB：案例知识库

**来源目录：**

```text
案例
案例仓库
```

**解决问题：**

- 真实客户是谁？
- 空间发生了什么？
- 用户原始需求是什么？
- 最终落地结果是什么？
- 哪些细节值得做内容？

**建议每个案例统一字段：**

```yaml
case_id:
项目名称:
面积:
城市:
家庭结构:
职业/生活方式:
核心需求:
关键行为:
空间问题:
使用材料:
使用工艺:
落地难点:
内容亮点:
可生成选题:
```

---

### 3.7 Content KB：内容生产知识库

**来源目录：**

```text
自媒体
风格手册
_extracted
模板
```

**解决问题：**

- 选题怎么做？
- 脚本怎么写？
- 拍摄怎么安排？
- 小红书/抖音怎么适配？
- 发布前怎么 QC？

**已有优势：**

`CLAUDE.md` 中已经有非常清晰的人设、禁用词、平台差异和内容工作流，可以直接作为内容 Agent 的“宪法”。

---

### 3.8 Human-Environment KB：人与环境观察知识库【建议新增】

**建议新增目录：**

```text
11_Human-Environment/
├── 需求/
│   ├── 安全感.md
│   ├── 掌控感.md
│   ├── 效率.md
│   ├── 连接.md
│   └── 意义.md
├── 行为/
│   ├── 放.md
│   ├── 拿.md
│   ├── 找.md
│   ├── 走.md
│   ├── 坐.md
│   └── 看.md
├── 环境/
│   ├── 光.md
│   ├── 声音.md
│   ├── 温度.md
│   ├── 材料.md
│   ├── 颜色.md
│   └── 空间形态.md
└── 系统/
    ├── 家庭系统.md
    ├── 工作系统.md
    ├── 学习系统.md
    ├── 收纳系统.md
    └── AI系统.md
```

**价值：**

这是连接 `studio-content` 和 `Human-Environment-Lab` 的关键层。

没有这一层，专业知识库只能回答“怎么做柜子”。

有了这一层，它可以回答：

```text
为什么人需要这个柜子？
这个柜子如何改变人的行为？
材料如何影响人的情绪？
空间如何塑造生活方式？
```

---

## 4. 每条知识点的 Agent 化模板

以后重要知识点不要只写成普通笔记，建议统一改成下面格式：

```yaml
id:
title:
category:
source_path:

entity_type:
  - 产品 / 材料 / 工艺 / 案例 / 行为 / 环境 / 系统

summary:

facts:
  - 

principles:
  - 

applicable_scenarios:
  - 

related_entities:
  - 

risks:
  - 

human_environment_mapping:
  needs:
    - 生存 / 效率 / 掌控 / 连接 / 意义
  behaviors:
    - 放 / 拿 / 找 / 等 / 走 / 坐 / 看
  environment_factors:
    - 光 / 声音 / 温度 / 材料 / 颜色 / 气味 / 空间形态 / AI
  systems:
    - 家庭 / 工作 / 学习 / 收纳 / 社交 / 财务 / AI

content_seeds:
  - title:
    angle:
    script_template:
    visual_suggestion:
```

---

## 5. Multi-Agent 角色设计

### 5.1 产品专家 Agent

读取：

```text
Product KB
Material KB
Craft KB
Delivery KB
```

输出：

- 产品解释
- 专业校验
- 风险判断
- 柜体系统拆解

---

### 5.2 材料研究员 Agent

读取：

```text
Material KB
Human-Environment KB
```

输出：

- 材料感官分析
- 材料情绪分析
- 材料与人格/职业/生活方式的组合
- 材料选题

---

### 5.3 工艺专家 Agent

读取：

```text
Craft KB
Delivery KB
```

输出：

- 工艺解释
- 施工风险
- 安装验收
- 避坑内容

---

### 5.4 案例拆解 Agent

读取：

```text
Case KB
Product KB
Human-Environment KB
```

输出：

- 案例亮点
- 用户需求拆解
- 内容选题
- 拍摄脚本

---

### 5.5 内容导演 Agent

读取：

```text
Content KB
Case KB
Human-Environment KB
```

输出：

- 口播脚本
- 画面清单
- 剪辑节奏
- 平台适配文案

---

### 5.6 商业策略 Agent

读取：

```text
Supply & Ops KB
Content KB
Case KB
```

输出：

- 服务产品设计
- 报价解释
- 责任边界
- 咨询产品包装

---

### 5.7 研究员 Agent

读取：

```text
Human-Environment KB
Observation Logs
Content Data
```

输出：

- 周度研究发现
- 高频主题
- 新框架
- 长期方向判断

---

## 6. 推荐重构后的目录结构

```text
studio-content/
├── 00_System/
│   ├── README.md
│   ├── CLAUDE.md
│   ├── Agent-Roles.md
│   └── Knowledge-Schema.md
│
├── 01_Product-KB/
├── 02_Material-KB/
├── 03_Craft-KB/
├── 04_Delivery-KB/
├── 05_Case-KB/
├── 06_Content-KB/
├── 07_Business-KB/
├── 08_Human-Environment-KB/
├── 09_Observation-Logs/
└── 10_Agent-Outputs/
```

注意：这不是让你马上大搬家。

第一阶段只需要新增：

```text
00_System/
08_Human-Environment-KB/
09_Observation-Logs/
```

原目录先不要动，避免打乱现有资料。

---

## 7. 下一步最小行动

不要一次性重构 1713 个文件。

只做三件事：

### 第一步：新增系统说明文件

```text
00_System/Knowledge-Schema.md
00_System/Agent-Roles.md
```

### 第二步：新增 Human-Environment 桥接层

```text
08_Human-Environment-KB/
```

### 第三步：从旧库里挑 10 个高价值知识点做 Agent 化改写

建议先选：

```text
封边
拉手
石英石
岩板
不锈钢台面
玄关柜
衣柜
餐边柜
水电交底
验收标准
```

这10个知识点能最快验证：

```text
专业知识
↓
Human-Environment框架
↓
内容生成
```

是否跑得通。

---

## 8. 核心判断

`studio-content` 是你的专业知识大脑。

`Human-Environment-Lab` 是你的研究大脑。

未来 Multi-Agent 系统要做的不是二选一，而是把两者连接：

```text
studio-content
提供专业事实

Human-Environment-Lab
提供观察框架

Multi-Agent
负责组合、检索、推理、生成内容
```

如果这个连接打通，你就不是在做一个普通自媒体知识库，而是在做一个可以长期生长的内容研究系统。

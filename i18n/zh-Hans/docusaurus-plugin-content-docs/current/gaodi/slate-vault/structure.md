---
sidebar_position: 2
title: 结构
---

# 结构

知识库有两个顶层文件夹。本页所有示例均使用虚构名称。

```text
brands/
projects/
```

## 品牌条目

一个文件夹对应一个品牌套件。

```text
brands/example-brand/
  guidelines.md
  palette.yml
  refs/
```

| 项 | 存放内容 |
|------|------|
| `guidelines.md` | 语气，以及文案的应做与禁做规则 |
| `palette.yml` | 按用途划分的颜色：primary、secondary、accent、neutral、background |
| `refs/` | 参考图：logo、产品图、场景图、包装图 |

品牌条目位于项目文件夹之外。项目所用的品牌在 Slate 中设置。Slate 在撰写 Listing 文案与营销图片时，会读取指南、配色与参考图。

## 项目条目

一个文件夹对应一个项目。

```text
projects/example-camera-12/
  project.md
  gen-1/
    design/
    analyse/
    voc/
    iterate/
    generate/
  uploads/
```

| 项 | 存放内容 |
|------|------|
| `project.md` | 项目记录：各项名称、型号、产品类目，以及提供给 Slate 的备注 |
| `gen-1/` | 该产品的第一个工作代次 |
| `uploads/` | 操作员提供的文件 |

## 代次

一个代次是对一个产品的一轮工作。代次从 1 开始编号。第二轮工作写入 `gen-2`，不会改动 `gen-1`。

## 阶段文件夹

每个代次下每个阶段各有一个文件夹。只有在某个阶段产出了文档之后，该阶段的文件夹才会出现。

| 文件夹 | 存放内容 |
|--------|------|
| `design` | 产品规格书 |
| `analyse` | 竞品数据集、差距分析、利润模型、电商平台 Listing 清单 |
| `voc` | 客户评论报告与产品问题分析 |
| `iterate` | 依据客户反馈修订的规格书 |
| `generate` | Listing 文案与营销图片 |

## 上传文件

上传的文件按提供时的原样保存在 `uploads` 中。Slate 不会改写它们。

每个 PDF、表格和 Word 文档在上传时会被读取一次。文本会以配套 Markdown 文件的形式写在原文件旁边，便于阅读与搜索。配套文件在 Slate 内的文件列表中不显示。

上传文件即使已被标记到某个代次和某个阶段，仍然留在 `uploads` 中。标记保存在 Slate 里，而不是文件夹名称中。

## 相关

- [概览](overview.md) 介绍访问权限与版本历史。
- [约定](conventions.md) 介绍命名与元数据。

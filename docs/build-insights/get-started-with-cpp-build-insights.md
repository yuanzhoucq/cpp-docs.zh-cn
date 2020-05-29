---
title: C++ 生成见解入门
description: 简要概述了 C++ 生成见解。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28d7e0758ea521af424129c546297fc97e3d6659
ms.sourcegitcommit: 8c8ed02a6f3bcb5ee008e3fe30ba7595d7c4c922
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2020
ms.locfileid: "83759220"
---
# <a name="get-started-with-c-build-insights"></a>C++ 生成见解入门

::: moniker range="<=vs-2017"

Visual Studio 2019 中提供 C++ 生成见解工具。 若要查看此版本对应的文档，请将本文的 Visual Studio“版本”选择器控件设置为“Visual Studio 2019”。 它位于此页面上目录表的顶部。

::: moniker-end
::: moniker range="vs-2019"

C++ 生成见解是一个工具集合，可便于更深入地了解 Microsoft Visual C++ (MSVC) 工具链。 这些工具收集与 C++ 生成相关的数据，并用一种有助于你回答常见问题的格式来呈现这些数据，比如：

- 我的生成是否已充分并行化？
- 我应在预编译头 (PCH) 中添加什么？
- 为了提高生成速度，是否有我应重点关注的特定瓶颈？

这项技术的主要组成部分包括：

- vcperf.exe：可用于收集生成跟踪的命令行实用工具；
- Windows Performance Analyzer (WPA) 扩展：可便于在 WPA 中查看生成跟踪；以及
- C++ 生成见解 SDK：软件开发工具包，用于创建你自己的工具来使用 C++ 生成见解数据。

## <a name="documentation-sections"></a>文档部分

[教程：vcperf 和 Windows Performance Analyzer](tutorials/vcperf-and-wpa.md)\
了解如何收集 C++ 项目的生成跟踪，以及如何在 WPA 中查看它们。

[教程：Windows 性能基础知识](tutorials/wpa-basics.md)\
发现用于分析生成跟踪的实用 WPA 使用技巧。

[C++ 生成见解 SDK](reference/sdk/overview.md)\
概述了 C++ 生成见解 SDK。

## <a name="articles"></a>文章

若要详细了解 C++ 生成见解，请阅读官方 C++ 团队博客中的以下文章：

[C++ 生成见解简介](https://devblogs.microsoft.com/cppblog/introducing-c-build-insights/)

[使用 C++ 生成见解 SDK 以编程方式分析生成](https://devblogs.microsoft.com/cppblog/analyze-your-builds-programmatically-with-the-c-build-insights-sdk/)

[根据 C++ 生成见解查找生成瓶颈](https://devblogs.microsoft.com/cppblog/finding-build-bottlenecks-with-cpp-build-insights/)

[使用根据 C++ 生成见解提出的 PCH 建议加速生成](https://devblogs.microsoft.com/cppblog/faster-builds-with-pch-suggestions-from-c-build-insights/)

::: moniker-end

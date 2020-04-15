---
title: C++ 生成见解入门
description: C++生成见解的高级概述。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3a75dfe3bf1263cce53d70b764607cad4eec86d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325719"
---
# <a name="get-started-with-c-build-insights"></a>C++ 生成见解入门

::: moniker range="<=vs-2017"

C++构建见解工具可在 Visual Studio 2019 中使用。 要查看该版本的文档，请将本文的可视化工作室**版本**选择器控件设置为 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range="vs-2019"

C++构建见解是一个工具的集合，可提高对 Microsoft 可视化C++ （MSVC） 工具链的可见性。 这些工具收集有关C++生成的数据，并以可帮助您回答常见问题的格式呈现数据，例如：

- 我的生成是否足够并行化？
- 我应该在预编译的标头 （PCH） 中包括哪些内容？
- 是否有特定的瓶颈我应该关注以提高我的生成速度？

该技术的主要组成部分是：

- *vcperf.exe，* 一个命令行实用程序，可用于收集生成的痕迹，
- 一个 Windows 性能分析器 （WPA） 扩展，允许您在 WPA 中查看生成跟踪，以及
- C++构建见解 SDK，这是一个软件开发工具包，用于创建使用C++生成见解数据的工具。

单击以下链接可快速启动这些组件：

[教程：vcperf 和 Windows 性能分析器](tutorials/vcperf-and-wpa.md)\
了解如何收集C++项目的生成跟踪，以及如何在 WPA 中查看它们。

[教程：Windows 性能基础知识](tutorials/wpa-basics.md)\
发现用于分析生成跟踪的有用 WPA 提示。

[C++构建见解 SDK](reference/sdk/overview.md)\
C++生成见解 SDK 的概述。

::: moniker-end

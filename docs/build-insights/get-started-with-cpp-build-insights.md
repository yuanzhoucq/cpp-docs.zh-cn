---
title: C++ 生成见解入门
description: 生成见解的C++高级概述。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a5799fecc885b96f4278e0f5077662ce5fd7c8f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332002"
---
# <a name="get-started-with-c-build-insights"></a>C++ 生成见解入门

::: moniker range="<=vs-2017"

Visual C++ Studio 2019 中提供了生成见解工具。 若要查看该版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 Visual Studio 2019。

::: moniker-end
::: moniker range="vs-2019"

C++Build Insights 是一系列工具，提供对 Microsoft Visual C++ （MSVC）工具链的更多可见性。 这些工具收集有关您C++的生成的数据，并以可以帮助您回答常见问题的格式提供这些信息，如：

- 我的生成是否足以并行化？
- 我应将预编译标头（PCH）包含哪些内容？
- 我是否应重点关注特定瓶颈以提高生成速度？

此技术的主要组件包括：

- *vcperf*是一个命令行实用工具，可用于收集生成的跟踪，
- 允许你在 WPA 中查看生成跟踪的 Windows 性能分析器（WPA）扩展，以及
- C++生成见解 SDK 是一个软件开发工具包，用于创建你自己的使用C++生成见解数据的工具。

单击下面的链接可快速开始处理以下组件：

[教程： vcperf 和 Windows 性能分析器](tutorials/vcperf-and-wpa.md)\
了解如何为你C++的项目收集生成跟踪以及如何在 WPA 中查看它们。

[教程： Windows 性能基础知识](tutorials/wpa-basics.md)\
发现用于分析生成跟踪的有用 WPA 提示。

生成见解 SDK\ [ C++ ](reference/sdk/overview.md)
C++生成见解 SDK 的概述。

::: moniker-end

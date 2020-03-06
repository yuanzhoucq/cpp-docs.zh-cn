---
title: 参考： vcperf 命令
description: 命令行实用工具 vcperf 的参考。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b85320ce4517eb41410c59a11bd79553405b8402
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333880"
---
# <a name="reference-vcperf-commands"></a>参考： vcperf 命令

::: moniker range="<=vs-2017"

Visual C++ Studio 2019 中提供了生成见解工具。 若要查看该版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 Visual Studio 2019。

::: moniker-end
::: moniker range="vs-2019"

本文列出并说明了*vcperf*中可用的命令以及如何使用它们。

## <a name="commands-to-start-and-stop-traces"></a>用于启动和停止跟踪的命令

*重要提示：以下命令都需要管理权限。*

| 选项           | 参数和说明 |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | 告诉*vcperf*在给定的会话名称下启动跟踪。 给定计算机上一次只能有一个活动会话。 <br/><br/> 如果指定 `/nocpusampling` 选项， *vcperf*将不收集 CPU 示例。 它禁止使用 Windows 性能分析器中的 "CPU 使用率" 视图，但会使收集的跟踪更小。 <br/><br/> 启动跟踪后， *vcperf*将立即返回。 对于在计算机上运行的所有进程，系统范围内收集事件。 这意味着你无需从与用于运行*vcperf*的命令提示符相同的命令提示符生成项目。 例如，你可以从 Visual Studio 生成项目。 |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | 停止由给定会话名称标识的跟踪。 在跟踪上运行后处理步骤，以生成在 Windows 性能分析器（WPA）中可查看的文件。 为了获得最佳的观看体验，请使用包含C++ Build Insights 外接程序的 WPA 版本。 有关详细信息，请参阅[ C++生成见解入门](/cpp/build-insights/get-started-with-cpp-build-insights)。 `<outputFile.etl>` 参数指定输出文件的保存位置。 |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | 停止由给定会话名称标识的跟踪，并将原始的未处理数据写入指定的输出文件中。 生成的文件并非应在 WPA 中查看。 <br/><br/> `/stop` 命令中涉及的后处理步骤有时会很长。 你可以使用 `/stopnoanalyze` 命令延迟此后处理步骤。 准备好生成可在 Windows 性能分析器中查看的文件时，请使用 `/analyze` 命令。 |

## <a name="miscellaneous-commands"></a>杂项命令

| 选项     | 参数和说明 |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | 接受 `/stopnoanalyze` 命令生成的原始跟踪文件。 在此跟踪上运行后处理步骤，以生成在 Windows 性能分析器中可查看的文件。 为了获得最佳的观看体验，请使用包含C++ Build Insights 外接程序的 WPA 版本。 有关详细信息，请参阅[ C++生成见解入门](/cpp/build-insights/get-started-with-cpp-build-insights)。 |

## <a name="see-also"></a>另请参阅

Build Insights\ 入门[ C++ ](/cpp/build-insights/get-started-with-cpp-build-insights)
[教程： Windows 性能分析器基础](/cpp/build-insights/tutorials/wpa-basics)\
[参考： Windows 性能分析器视图](wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end

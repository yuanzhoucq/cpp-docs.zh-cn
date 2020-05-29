---
title: 参考： vcperf 命令
description: 命令行实用程序 vcperf.exe 的引用。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9d3b0a9dbdfe922dc87f91006441e1f65d54c8a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323243"
---
# <a name="reference-vcperf-commands"></a>参考： vcperf 命令

::: moniker range="<=vs-2017"

C++构建见解工具可在 Visual Studio 2019 中使用。 要查看该版本的文档，请将本文的可视化工作室**版本**选择器控件设置为 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range="vs-2019"

本文列出并描述了*vcperf.exe*中可用的命令，以及如何使用它们。

## <a name="commands-to-start-and-stop-traces"></a>开始和停止跟踪的命令

*重要提示：以下命令都需要管理权限。*

| 选项           | 参数和描述 |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | 告诉*vcperf.exe*在给定会话名称下启动跟踪。 给定计算机上一次只能有一个活动会话。 <br/><br/> 如果指定`/nocpusampling`了该选项 *，vcperf.exe*不会收集 CPU 样本。 它可以防止在 Windows 性能分析器中使用 CPU 使用率（采样）视图，但会使收集的跟踪变小。 <br/><br/> 开始跟踪后 *，vcperf.exe*会立即返回。 对于在计算机上运行的所有进程，将系统范围内收集事件。 这意味着您不需要从与运行*vcperf.exe*的命令提示相同的命令提示生成项目。 例如，可以从可视化工作室构建项目。 |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | 停止由给定会话名称标识的跟踪。 在跟踪上运行后处理步骤，以生成 Windows 性能分析器 （WPA） 中可查看的文件。 为获得最佳查看体验，请使用包含C++生成见解外接程序的 WPA 版本。 有关详细信息，请参阅[开始C++生成见解](/cpp/build-insights/get-started-with-cpp-build-insights)。 参数`<outputFile.etl>`指定保存输出文件的位置。 |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | 停止给定会话名称标识的跟踪，并在指定的输出文件中写入原始未处理的数据。 生成的文件不应在 WPA 中查看。 <br/><br/> `/stop`命令中涉及的后处理步骤有时可能很长。 可以使用 命令`/stopnoanalyze`延迟此后处理步骤。 准备好在`/analyze`Windows 性能分析器中生成可查看的文件时，请使用 该命令。 |

## <a name="miscellaneous-commands"></a>杂项命令

| 选项     | 参数和描述 |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | 接受`/stopnoanalyze`命令生成的原始跟踪文件。 在此跟踪上运行后处理步骤，以生成 Windows 性能分析器中可查看的文件。 为获得最佳查看体验，请使用包含C++生成见解外接程序的 WPA 版本。 有关详细信息，请参阅[开始C++生成见解](/cpp/build-insights/get-started-with-cpp-build-insights)。 |

## <a name="see-also"></a>另请参阅

[开始C++构建见解](/cpp/build-insights/get-started-with-cpp-build-insights)\
[教程：Windows 性能分析器基础知识](/cpp/build-insights/tutorials/wpa-basics)\
[参考：Windows 性能分析器视图](wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end

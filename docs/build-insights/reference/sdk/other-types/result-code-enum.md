---
title: RESULT_CODE枚举
description: C++生成见解 SDK RESULT_CODE枚举引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RESULT_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 62874e176c3f3e8f9df1ca64e7b593b7a0ef5c01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323625"
---
# <a name="result_code-enum"></a>RESULT_CODE枚举

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

枚`RESULT_CODE`举描述了成功和失败的情况。

## <a name="members"></a>成员

| “属性” | “值” | 说明 |
|--|--|--|
| `RESULT_CODE_SUCCESS` | 0 （0x000000） | 操作成功。 |
| `RESULT_CODE_FAILURE_ANALYSIS_ERROR` | 1 (0x00000001) | [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)中的回调函数之一返回该`CALLBACK_CODE_ANALYSIS_FAILURE`值。 此值是[CALLBACK_CODE](callback-code-enum.md)枚举的成员。 |
| `RESULT_CODE_FAILURE_CANCELLED` | 2 （0x0000002） | [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)中的回调函数之一返回该`CALLBACK_CODE_ANALYSIS_CANCEL`值。 此值是[CALLBACK_CODE](callback-code-enum.md)枚举的成员。 |
| `RESULT_CODE_FAILURE_INVALID_INPUT_LOG_FILE` | 3 （0x0000003） | 指定的 Windows （ETW） 跟踪的输入事件跟踪无效。 |
| `RESULT_CODE_FAILURE_INVALID_OUTPUT_LOG_FILE` | 4 （0x0000004） | 指定的输出 ETW 跟踪无效。 |
| `RESULT_CODE_FAILURE_MISSING_ANALYSIS_CALLBACK` | 5 （0x0000005） | [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)结构未正确初始化。 |
| `RESULT_CODE_FAILURE_MISSING_RELOG_CALLBACK` | 6 （0x0000006） | [RELOG_CALLBACKS](relog-callbacks-struct.md)结构未正确初始化。 |
| `RESULT_CODE_FAILURE_OPEN_INPUT_TRACE` | 7 （0x0000007） | 无法打开输入 ETW 跟踪。 |
| `RESULT_CODE_FAILURE_PROCESS_TRACE` | 8 （0x0000008） | 处理输入 ETW 跟踪时出错。 |
| `RESULT_CODE_FAILURE_START_RELOGGER` | 9 （0x0000009） | 尝试启动重新登录会话时出错。 |
| `RESULT_CODE_FAILURE_DROPPED_EVENTS` | 10 （0x0000000A） | 输入 ETW 跟踪缺少重要事件。 |
| `RESULT_CODE_FAILURE_UNSUPPORTED_OS` | 11 （0x000000B） | 您正在不受支持的 Windows 版本上使用C++生成见解。 |
| `RESULT_CODE_FAILURE_INVALID_TRACING_SESSION_NAME` | 12 （0x000000C） | 提供的会话名称无效。 |
| `RESULT_CODE_FAILURE_INSUFFICIENT_PRIVILEGES` | 13 （0x000000D） | 此操作需要管理员权限。 |
| `RESULT_CODE_FAILURE_GENERATE_GUID` | 14 （0x0000000E） | 生成 GUID 时出错。 |
| `RESULT_CODE_FAILURE_OBTAINING_TEMP_DIRECTORY` | 15 （0x0000000F） | 尝试确定临时目录路径时出错。 |
| `RESULT_CODE_FAILURE_CREATE_TEMPORARY_DIRECTORY` | 16 （0x0000010） | 尝试为正在启动的跟踪会话创建临时目录时出错。 |
| `RESULT_CODE_FAILURE_START_SYSTEM_TRACE` | 17 （0x00000011） | 尝试启动系统跟踪时出错。 |
| `RESULT_CODE_FAILURE_START_MSVC_TRACE` | 18 （0x00000012） | 尝试启动 MSVC 跟踪时出错。 |
| `RESULT_CODE_FAILURE_STOP_MSVC_TRACE` | 19 （0x00000013） | 尝试停止 MSVC 跟踪时出错。 |
| `RESULT_CODE_FAILURE_STOP_SYSTEM_TRACE` | 20 （0x00000014） | 尝试启动系统跟踪时出错。 |
| `RESULT_CODE_FAILURE_SESSION_DIRECTORY_RESOLUTION` | 21 （0x00000015） | 跟踪已停止，但找不到跟踪会话的临时目录。 |
| `RESULT_CODE_FAILURE_MSVC_TRACE_FILE_NOT_FOUND` | 22 （0x00000016） | 找不到已停止的 MSVC 跟踪的跟踪文件。 |
| `RESULT_CODE_FAILURE_MERGE_TRACES` | 23 （0x00000017） | 使用内核跟踪控件合并跟踪时出错。 |
| `RESULT_CODE_FAILURE_UNKNOWN_ERROR` | 24 （0x00000018） | 发生未知错误。 |

::: moniker-end

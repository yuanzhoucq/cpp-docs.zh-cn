---
title: runtime_function 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f3831dc36664c556cf0a020ed87c60200443fd3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718232"
---
# <a name="struct-runtimefunction"></a>RUNTIME_FUNCTION 结构

基于表的异常处理的分配堆栈空间或调用另一个函数 （例如，非叶函数） 的所有功能要求表条目。 函数表条目具有以下格式：

|||
|-|-|
|ULONG|函数起始地址|
|ULONG|函数结束地址|
|ULONG|展开信息地址|

Runtime_function 结构结构必须对齐在内存中的 DWORD。 所有地址都是相对的映像，也就是说，它们都是相对于包含函数表项的图像的起始地址的 32 位偏移量。 这些项排序，放入 PE32 + 映像的.pdata 部分。 对于动态生成的函数 [JIT 编译器]，运行时以支持这些函数必须使用 RtlInstallFunctionTableCallback 或 RtlAddFunctionTable 来向操作系统提供此信息。 如果不这样做将导致不可靠的异常处理和调试的进程。

## <a name="see-also"></a>请参阅

[为异常处理和调试器支持展开数据](../build/unwind-data-for-exception-handling-debugger-support.md)
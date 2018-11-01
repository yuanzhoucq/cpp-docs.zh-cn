---
title: RUNTIME_FUNCTION 结构
ms.date: 11/04/2016
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
ms.openlocfilehash: 6b113f6cf1e9951f9e4578e15c9ed0af3d036fa6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520241"
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
---
title: runtime_function 结构 |Microsoft 文档
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
ms.openlocfilehash: 3c2f28380d4a14cf7617653ede20468c45649a8b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379921"
---
# <a name="struct-runtimefunction"></a>RUNTIME_FUNCTION 结构
基于表的异常处理的分配堆栈空间或调用另一个函数 （例如，非叶函数） 的所有函数需要一个表项。 函数表项具有格式：  
  
|||  
|-|-|  
|ULONG|函数起始地址|  
|ULONG|函数结束地址|  
|ULONG|展开信息地址|  
  
 Runtime_function 结构结构必须在内存中的对齐的 DWORD。 所有的地址是相对的映像，也就是说，它们将从包含函数表项的映像的起始地址的 32 位偏移量。 这些项排序，并且将放入 PE32 + 映像的.pdata 部分。 对于动态生成的函数 [JIT 编译器]，运行时以支持这些函数必须使用 RtlInstallFunctionTableCallback 或 RtlAddFunctionTable 将此信息提供给操作系统。 如果不这样做将导致不可靠的异常处理和调试的进程。  
  
## <a name="see-also"></a>请参阅  
 [为异常处理和调试器支持展开数据](../build/unwind-data-for-exception-handling-debugger-support.md)
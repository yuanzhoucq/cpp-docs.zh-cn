---
title: 链式展开信息结构
ms.date: 11/04/2016
ms.assetid: 176835bf-f118-45d9-9128-9db4b7571864
ms.openlocfilehash: 19d0beb8c3438183fa594d7ec3cab4929b3a491a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502136"
---
# <a name="chained-unwind-info-structures"></a>链式展开信息结构

如果设置 UNW_FLAG_CHAININFO 标志，则展开信息结构是一个辅助和共享的异常处理程序/链接在一起的信息地址字段包含主展开信息。 以下代码检索主展开的信息，前提假设`unwindInfo`是结构，它具有 UNW_FLAG_CHAININFO 标志设置。

```
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

链接的信息是在两种情况下很有用。 首先，它可以用于非连续的代码段。 通过使用链接的信息，可以减少需要的展开信息的大小，因为您不需要重复主展开信息中的展开代码数组。

此外可以使用链接的信息进行分组易失寄存器保存。 编译器可能会延迟保存一些易失寄存器，直至这不在函数入口 prolog。 您可以通过主展开信息之前分组的代码，该函数的部分记录这，然后设置链式与序言中，其中链接信息中的展开代码反映非易失性寄存器的保存的非零大小的信息。 在这种情况下，展开代码是 UWOP_SAVE_NONVOL 的所有实例。 不支持的分组，它将非易失寄存器保存通过使用请求或使用其他固定的堆栈分配修改 RSP 注册。

Unwind_info 结构项具有 UNW_FLAG_CHAININFO 设置可以包含其 unwind_info 结构的项也具有 UNW_FLAG_CHAININFO 设置 （多个紧缩） runtime_function 结构项。 最终，链式展开信息指针将到达具有 UNW_FLAG_CHAININFO 清除; unwind_info 结构项这是主 unwind_info 结构项目，指向实际过程入口点。

## <a name="see-also"></a>请参阅

[为异常处理和调试器支持展开数据](../build/unwind-data-for-exception-handling-debugger-support.md)
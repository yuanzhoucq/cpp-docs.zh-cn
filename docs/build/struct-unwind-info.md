---
title: UNWIND_INFO 结构
ms.date: 11/04/2016
ms.assetid: f0aee906-a1b9-44cc-a8ad-463637bd5411
ms.openlocfilehash: 0130d30c314a7736ffaf24753a2e6fdf9ad55b12
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517034"
---
# <a name="struct-unwindinfo"></a>UNWIND_INFO 结构

展开数据信息结构用于记录的函数有堆栈指针和非易失寄存器在堆栈上的保存位置的影响：

|||
|-|-|
|UBYTE: 3|版本|
|UBYTE: 5|Flags|
|UBYTE|序言的大小|
|UBYTE|展开代码的计数|
|UBYTE: 4|帧寄存器|
|UBYTE: 4|帧寄存器偏移量 （缩放）|
|USHORT \* n|展开代码数组|
|变量|可以是窗体的 （1） 或 （2） 下面|

（1） 异常处理程序

|||
|-|-|
|ULONG|异常处理程序的地址|
|变量|特定于语言的处理程序数据 （可选）|

（2） 链式展开信息

|||
|-|-|
|ULONG|函数起始地址|
|ULONG|函数结束地址|
|ULONG|展开信息地址|

UNWIND_INFO 结构必须对齐在内存中的 DWORD。 每个字段的含义如下所示：

- **Version**

   展开数据，当前为 1 的版本号。

- **标志**

   当前定义三个标记：

   |Flag|描述|
   |-|-|
   |`UNW_FLAG_EHANDLER`| 该函数具有寻找需要检查异常的函数时，应调用的异常处理程序。|
   |`UNW_FLAG_UHANDLER`| 该函数具有展开异常时，应调用终止处理程序。|
   |`UNW_FLAG_CHAININFO`| 此展开信息结构不是主要的过程。 相反，连锁展开项是上一 runtime_function 结构项的内容的信息。 请参阅以下有关的说明文本链式展开信息结构。 如果设置此标志，则必须清除 UNW_FLAG_EHANDLER 和 UNW_FLAG_UHANDLER 标志。 此外，框架注册和已修复堆栈分配字段必须具有相同的值如下所示主展开信息。|

- **序言的大小**

   函数序言中以字节为单位的长度。

- **展开代码的计数**

   这是指向展开代码数组中的槽数。 请注意某些展开代码 (例如，UWOP_SAVE_NONVOL) 需要数组中的多个槽。

- **帧寄存器**

   如果非零值，然后该函数使用帧指针，并且该字段用作帧指针，使用相同的编码表示的操作信息字段的 unwind_code 结构节点的非易失性寄存器的数量。

- **框架注册偏移量 （缩放）**

   如果帧注册字段为非零值，这是相对于其建立时应用于 FP reg RSP 缩放偏移量。 实际的 FP reg 设置为 RSP + 16\*此编号，允许从 0 到 240 之间的偏移量。 这将允许 FP reg 指向动态堆栈帧，允许更好的代码密度较短的指令 （详细说明可以使用 8 位有符号偏移量窗体） 通过本地堆栈分配的中间。

- **展开代码数组**

   这是一个数组项上的非易失寄存器和 RSP 解释序言的效果。 请参阅 unwind_code 结构上的各个项的含义。 出于对齐目的，此数组将始终具有偶数数目的项，可能未使用的最后一项 （在这种情况下该数组将是一个长度超过所指示的值的展开代码字段计数）。

- **异常处理程序的地址**

   这是指向函数的特定于语言的异常/终止处理程序的映像相对指针 （如果清除标志 UNW_FLAG_CHAININFO 且 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER 的标志已设置）。

- **特定于语言的处理程序的数据**

   这是函数的特定于语言的异常处理程序数据。 此数据的格式是未指定，并完全由正在使用的特定异常处理程序。

- **链式展开信息**

   如果设置了标志 UNW_FLAG_CHAININFO UNWIND_INFO 结构以三个 UWORDs 结尾。  这些 UWORDs 表示该函数的 runtime_function 结构信息的链接展开。

## <a name="see-also"></a>请参阅

[为异常处理和调试器支持展开数据](../build/unwind-data-for-exception-handling-debugger-support.md)
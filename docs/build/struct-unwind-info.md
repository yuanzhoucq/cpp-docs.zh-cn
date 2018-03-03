---
title: "unwind_info 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: f0aee906-a1b9-44cc-a8ad-463637bd5411
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1effec5bc753f1b23f8d43a8406c61cb6663fa56
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="struct-unwindinfo"></a>UNWIND_INFO 结构
展开数据信息结构用于记录的函数具有的堆栈指针和非易失寄存器在堆栈上的保存位置的影响：  
  
|||  
|-|-|  
|UBYTE: 3|版本|  
|UBYTE: 5|Flags|  
|UBYTE|序言的大小|  
|UBYTE|展开代码的计数|  
|UBYTE: 4|帧寄存器|  
|UBYTE: 4|帧寄存器偏移量 （缩放）|  
|USHORT * n|展开代码数组|  
|变量|可以是窗体 （1） 或 （2） 下面|  
  
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
  
 UNWIND_INFO 结构必须在内存中的对齐的 DWORD。 每个字段的含义是，如下所示：  
  
 **Version**  
 展开数据，当前 1 版本号。  
  
 **标志**  
 当前定义三个标记：  
  
 UNW_FLAG_EHANDLER 函数有查找需要检查异常的函数时应调用异常处理程序。  
  
 UNW_FLAG_UHANDLER 函数具有展开异常时应调用终止处理程序。  
  
 UNW_FLAG_CHAININFO 这展开信息结构不是在主过程。 相反，连锁展开条目是上一个 runtime_function 结构项的内容的信息。 请参阅以下有关的说明文本链式展开信息结构。 如果设置此标志，则必须清除 UNW_FLAG_EHANDLER 和 UNW_FLAG_UHANDLER 标志。 此外，框架注册和固定堆栈分配字段必须具有相同的值如下所示主展开信息。  
  
 **序言的大小**  
 函数序言中以字节为单位的长度。  
  
 **展开代码的计数**  
 这是展开代码数组中的槽的数量。 请注意一些展开代码 (例如，UWOP_SAVE_NONVOL) 需要数组中的多个槽。  
  
 **帧寄存器**  
 如果不为零，则函数使用帧指针，并且该字段为用作帧指针，使用相同的编码表示的操作信息字段 UNWIND_CODE 节点的非易失寄存器的数目。  
  
 **帧寄存器 （缩放） 的偏移量**  
 如果帧寄存器字段不为零，则这是从它建立时应用于 FP reg RSP 缩放后的偏移量。 实际的 FP reg 设置为 RSP + 16 * 此数字，允许从 0 到 240 之间的偏移量。 这允许 FP reg 指向动态堆栈帧，允许通过较短的指令 （详细说明可以使用 8 位有符号偏移量的格式） 的更好代码密度本地堆栈分配的中间。  
  
 **展开代码数组**  
 这是解释序言的效果的非易失寄存器和 RSP 项的数组。 有关的各项的含义，请参阅 UNWIND_CODE 一节。 对于对齐的目的，此数组将始终具有偶数数目的项，与可能未使用的最后一项 （在这种情况下该数组将是一个长度超过所指示的值的展开代码字段的计数）。  
  
 **异常处理程序的地址**  
 这是指向函数的特定于语言的异常/终止处理程序的映像相对指针 （如果清除标志 UNW_FLAG_CHAININFO 且标记 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER 之一设置）。  
  
 **特定于语言的处理程序数据**  
 这是函数的特定于语言的异常处理程序数据。 此数据的格式是未指定，并且完全由中使用的特定异常处理程序。  
  
 **链式展开信息**  
 如果设置标志 UNW_FLAG_CHAININFO UNWIND_INFO 结构结尾三个 UWORDs。  这些 UWORDs 表示函数的 runtime_function 结构信息的链接展开。  
  
## <a name="see-also"></a>请参阅  
 [为异常处理和调试器支持展开数据](../build/unwind-data-for-exception-handling-debugger-support.md)
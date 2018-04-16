---
title: "展开过程 |Microsoft 文档"
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
ms.assetid: 82c5d0ca-70be-4d1a-a306-bfe01c29159f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b8caa2be1528c26cf374637f3d0357847721de9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="unwind-procedure"></a>展开过程
展开代码数组按降序排列。 发生异常时，上下文记录中的操作系统存储的完整上下文。 然后调用异常调度逻辑，这其中重复执行以下步骤以查找异常处理程序。  
  
1.  使用存储在上下文记录当前 RIP 搜索 runtime_function 结构表条目，用于描述当前函数 （或函数部分，在链接 unwind_info 结构项的情况下）。  
  
2.  如果不找到任何函数的表项，则在叶函数中，并 RSP 将直接解决返回的指针。 在 [RSP] 返回的指针存储在更新后的上下文、 模拟的 RSP 就会递增 8，和重复步骤 1。  
  
3.  如果找到函数表条目，则 RIP 后可以位于在三个区域） 在 epilog、 b） 在序言中，或 c） 在可能覆盖的异常处理程序代码中。  
  
    -   大小写) 如果 RIP 位于 epilog，则控件离开此函数，可能没有与此函数，此异常关联的异常处理程序并且必须继续 epilog 的影响来计算调用方函数的上下文。 若要确定 RIP 是否在范围内的 epilog 代码流从 RIP 上检查。 如果该代码流，可以匹配到合法 epilog，尾随部分则位于 epilog 和模拟 epilog 的剩余部分，使用更新为每个指令的上下文记录进行处理。 此后，重复步骤 1。  
  
    -   案例 b） 如果 RIP 内序言，则控制尚未存在于输入函数，可以有没有与此函数，此异常关联的异常处理程序且必须撤消序言的效果来计算调用方函数的上下文。 RIP 都在序言内，如果从函数开始到 RIP 的距离小于或等于 prolog 大小中的展开信息编码。 序言的效果是展开前扫描通过的偏移量小于或等于函数开始时，请从 RIP 的偏移量的第一个条目的展开代码数组然后撤消展开代码数组中的所有剩余项的效果。 然后重复步骤 1。  
  
    -   案例 c) 如果 RIP 不在 prolog 或 epilog 和函数内具有 （设置 UNW_FLAG_EHANDLER） 的异常处理程序，则调用语言特定的处理程序。 该处理程序扫描其数据和调用筛选器与相应的功能。 处理了该异常或所必须继续进行搜索，可以返回语言特定的处理程序。 它可以直接启动展开。  
  
4.  如果语言特定的处理程序返回处理的状态，则继续执行使用原始的上下文记录。  
  
5.  如果没有任何语言特定的处理程序，或者处理程序返回"继续搜索"状态，上下文记录必须展开到调用方的状态。 这是通过处理所有撤消上的效果的展开代码数组元素实现的。 然后重复步骤 1。  
  
 链式展开信息涉及，仍然遵循以下基本步骤。 唯一的区别是，遍历要展开序言的效果，一旦达到该数组末尾的展开代码数组，它然后链接到父展开信息而存在整个展开代码数组将遍历。 此链接将继续，直到到达不 UNW_CHAINED_INFO 标志展开信息和完成遍历其展开代码数组。  
  
 最小部分的展开数据是 8 个字节。 这可能表示的函数，仅分配 128 个字节的堆栈或更少，并可能保存了一个非易失寄存器。 这也是大小的链式展开信息结构零长度 prolog 与未展开代码。  
  
## <a name="see-also"></a>请参阅  
 [异常处理 (x64)](../build/exception-handling-x64.md)
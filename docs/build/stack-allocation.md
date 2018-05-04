---
title: 堆栈分配 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098e51f2-eda6-40d0-b149-0b618aa48b47
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: caa6d435db98c7177cbf55b866bb8e5a4a110c1d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="stack-allocation"></a>堆栈分配
函数的 prolog 负责为本地变量分配堆栈空间，保存的寄存器，堆栈参数，并注册参数。  
  
 参数区域始终在堆栈底部 （即使是使用 alloca），以便它始终会靠近的寄信人地址的任何函数调用过程。 它包含至少四个条目，但足够空间来保留所有参数始终需要的不能调用任何函数。 请注意，即使参数本身永远不会托管到堆栈; 始终将寄存器参数，为分配空间被调用方不保证所有其参数的分配空间。 这样的相邻区域才可以使用被调用的函数需要采用自变量列表 (va_list) 或单个自变量的地址的情况下，家庭地址所需的寄存器自变量。 此区域还提供了方便的位置，若要在转换 （thunk） 执行期间以及作为调试选项保存寄存器自变量 （例如，它将自变量便于查找在调试如果它们存储在其在 prolog 代码中的家庭地址期间）。 即使被调用的函数具有少于 4 个参数，这些 4 堆栈位置有效地归调用函数，并可能被调用函数使用保存寄存器值的参数以外的其他目的。  因此调用方可能未将信息保存在此区域堆栈整个函数调用。  
  
 如果动态分配空间 (alloca) 函数中，然后非易失寄存器必须用作帧指针以将标记固定堆栈的一部分的基寄存器必须且保存在序言中初始化。 请注意，当使用 alloca 时，从相同的调用方对相同的被调用方的调用可能有不同的内部地址寄存器参数。  
  
 堆栈将始终保持不变 16 字节对齐中 （例如，在推送到的回邮地址），prolog, except 和中所示除外[函数类型](../build/function-types.md)对于帧函数某一类。  
  
 下面是一个函数的调用非叶 where 函数 B.函数 A 的序言堆栈布局的示例已为所有寄存器和堆栈所都需的参数在堆栈底部 B 分配了空间。 该调用将返回地址和 B 的 prolog 为其本地变量、 非易失寄存器和它调用的函数所需的空间分配空间。 如果 B 使用 alloca，是本地的变量/非易失寄存器保存区和参数堆栈区域之间分配空间。  
  
 ![AMD 转换示例](../build/media/vcamd_conv_ex_5.png "vcAmd_conv_ex_5")  
  
 当函数 B 调用另一个函数时，寄信人地址的正下方的家庭地址按以 RCX 中。  
  
## <a name="see-also"></a>请参阅  
 [堆栈使用](../build/stack-usage.md)
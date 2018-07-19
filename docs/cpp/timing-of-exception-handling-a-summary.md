---
title: 异常处理的计时： 摘要 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- sequence [C++]
- sequence, of handlers
- exception handling [C++], timing
- setjmpex.h
- termination handlers [C++], timing
- setjmp.h
- handlers [C++], order of exception
- structured exception handling [C++], timing
ms.assetid: 5d1da546-73fd-4673-aa1a-7ac0f776c420
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff2ac5abb13ae700e464635efc90a91c4a5835ab
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939411"
---
# <a name="timing-of-exception-handling-a-summary"></a>异常处理的计时：摘要
终止处理程序执行了无论 **__try**终止语句块。 原因包括跳出 **__try**块中，`longjmp`语句将控制权传出块和异常处理而堆栈展开。  
  
> [!NOTE]
>  Visual C++ 支持 `setjmp` 和 `longjmp` 语句两种形式。 快速版本会跳过终止处理，但更高效。 若要使用此版本，包括文件\<setjmp.h >。 另一个版本支持上一段中所述的终止处理。 若要使用此版本，包括文件\<setjmpex.h >。 快速版本的性能提升取决于硬件配置。  
  
 在执行任何其他代码前，操作系统将以适当的顺序执行所有终止处理程序，包括异常处理程序的主体。  
  
 当中断的原因是异常时，系统在决定要终止的内容前必须先执行一个或多个异常处理程序的筛选器部分。 事件的顺序如下：  
  
1.  引发异常。  
  
2.  系统查看活动异常处理程序的层次结构并执行具有最高优先级的处理程序的筛选器；从块和函数调用来看，这是最新安装且嵌套最深的异常处理程序。  
  
3.  如果此筛选器传递控制权（返回 0），过程将继续，直到发现筛选器不传递控制权。  
  
4.  如果此筛选器返回-1，继续执行，其中引发了异常，并且不会发生终止。  
  
5.  如果筛选器返回 1，则发生以下事件：  
  
    -   系统展开堆栈，以清除当前执行的代码之间的所有堆栈帧（引发异常处）以及包含获取控制权的异常处理程序的堆栈帧。  
  
    -   当堆栈展开时，堆栈上的所有终止处理程序都将执行。  
  
    -   执行异常处理程序本身。  
  
    -   控制权将交给此异常处理程序末尾后的代码行。  
  
## <a name="see-also"></a>请参阅  
 [编写终止处理程序](../cpp/writing-a-termination-handler.md)   
 [结构化异常处理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
---
title: 堆栈使用情况 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6f711636089a6f2966002002220aac88cebe17a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379853"
---
# <a name="stack-usage"></a>堆栈使用
超出 RSP 的当前地址的所有内存均都视为可变： 操作系统或调试器，可能会在用户调试会话或中断处理程序期间覆盖此内存。 因此，RSP 必须始终设置然后再尝试读取或写入到堆栈帧的值。  
  
 本部分讨论的本地变量的堆栈空间分配和**alloca**内部函数。  
  
-   [堆栈分配](../build/stack-allocation.md)  
  
-   [构造动态的参数堆栈区域](../build/dynamic-parameter-stack-area-construction.md)  
  
-   [函数类型](../build/function-types.md)  
  
-   [malloc 对齐](../build/malloc-alignment.md)  
  
-   [alloca](../build/alloca.md)  
  
## <a name="see-also"></a>请参阅  
 [x64 软件约定](../build/x64-software-conventions.md)
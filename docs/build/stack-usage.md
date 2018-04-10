---
title: 堆栈使用情况 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d6e3aa8d01dcc85b6c37684ccccaf82c84d8dfb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
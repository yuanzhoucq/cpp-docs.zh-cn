---
title: 2.9 指令嵌套 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28e690ba531b4b37973bc2555d904317181ff918
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="29-directive-nesting"></a>2.9 指令嵌套
动态嵌套指令必须遵守以下规则：  
  
-   A**并行**动态在另一个指令**并行**逻辑上建立启用新的团队，这组成仅当前线程，除非嵌套并行度。  
  
-   **有关**，**部分**，和**单个**将绑定到相同的指令**并行**不允许嵌套在每个其他。  
  
-   **关键**不允许嵌套在相互具有相同名称的指令。 请注意此限制不足以防止死锁。  
  
-   **有关**，**部分**，和**单个**指令不允许使用的动态程度**关键**，**排序**，和**master**如果指令将绑定到相同的区域**并行**作为区域。  
  
-   **屏障**指令不允许使用的动态程度**为**，**排序**，**部分**，**单个**， **master**，和**关键**如果指令将绑定到相同的区域**并行**作为区域。  
  
-   **主**指令不允许使用的动态程度**为**，**部分**，和**单个**指令如果**master**指令将绑定到相同**并行**作为工作共享指令。  
  
-   **排序**指令不允许在动态范围内的**关键**如果指令将绑定到相同的区域**并行**作为区域。  
  
-   时执行并行区域外，还允许任何时并行区域内动态执行允许的指令。 执行时动态用户指定的并行区域外，通过团队组成只有主线程执行的指令。
---
title: "2.6.3 barrier 指令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: adc480a82668da3c3ad7fdb88a701b3fa80ae9e3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="263-barrier-directive"></a>2.6.3 barrier 指令
**屏障**指令会同步组中的所有线程。 在遇到时，团队中的每个线程等待，直到所有其他已达到此点。 语法**屏障**指令是，如下所示：  
  
```  
#pragma omp barrier new-line  
```  
  
 团队中的所有线程都遇到屏障后，团队中的每个线程开始后的屏障指令中并行执行语句。 请注意，因为**屏障**指令不具有 C 语言语句作为其语法的一部分，有一些限制它在程序中的放置位置。 请参阅[附录 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)正式语法。 下面的示例阐释了这些限制。  
  
```  
/* ERROR - The barrier directive cannot be the immediate  
*          substatement of an if statement  
*/  
if (x!=0)  
   #pragma omp barrier  
...  
  
/* OK - The barrier directive is enclosed in a  
*      compound statement.  
*/  
if (x!=0) {  
   #pragma omp barrier  
}  
```
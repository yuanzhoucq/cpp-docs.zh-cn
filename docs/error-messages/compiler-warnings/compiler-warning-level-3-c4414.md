---
title: 编译器警告 （等级 3） C4414 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4414
dev_langs:
- C++
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1526b20732d7a1b08ec8d753cb64e33e42dd809
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289703"
---
# <a name="compiler-warning-level-3-c4414"></a>编译器警告（等级 3）C4414
function： 短跳转到函数转换到接近  
  
 短跳转生成 compact 指令从指令分支到限制范围之内的地址。 该指令包括短的偏移量表示该跳转的目标地址，函数定义之间的距离。 在链接期间函数可能会导致函数退出访问的范围从短的偏移量的移动或进行链接时优化。 编译器必须生成的跳转，这需要近或远 jmp 指令的特殊记录。 编译器进行了此转换。  
  
 例如，下面的代码生成 C4414:  
  
```  
// C4414.cpp  
// compile with: /W3 /c  
// processor: x86  
int DoParityEven();  
int DoParityOdd();  
unsigned char global;  
int __declspec(naked) DoParityEither()  
{  
   __asm  
   {  
      test global,0  
      jpe SHORT DoParityEven  // C4414  
      jmp SHORT DoParityOdd   // C4414  
   }  
}  
```
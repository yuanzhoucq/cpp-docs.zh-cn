---
title: 编译器警告 （等级 1） C4556 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- xml
- C4556
dev_langs:
- C++
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22d10f7dc73e0d5e39fcad8975114f7cb176b24d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282907"
---
# <a name="compiler-warning-level-1-c4556"></a>编译器警告（等级 1）C4556
内部函数的即时自变量 value 的值超出了范围下限的上限  
  
 内部函数匹配硬件指令。 硬件指令具有固定的数量的位进行编码常量。 如果***值***是超出范围，它会不编码正确。 编译器将截断的额外的位。  
  
 下面的示例生成 C4556:  
  
```  
// C4556.cpp  
// compile with: /W1  
// processor: x86 IPF  
#include <xmmintrin.h>  
void test()  
{  
   __m64 m;  
   _m_pextrw(m, 5);   // C4556  
}  
int main()  
{  
}  
```
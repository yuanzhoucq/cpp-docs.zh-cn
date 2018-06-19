---
title: 编译器警告 （等级 4） C4937 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4937
dev_langs:
- C++
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ed7b33889677a304d303873799f36430c38129a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294926"
---
# <a name="compiler-warning-level-4-c4937"></a>编译器警告（等级 4）C4937
“text1”和“text2”作为“directive”的参数时不可区分  
  
 由于编译器处理指令的参数的方式不同，无法区分对编译器具有意义的名称，如具有多文本表现形式（单下划线或双下划线形式）的关键字。  
  
 此类字符串的示例包括 __cdecl 和\__forceinline。  请注意，在 /Za 下，仅双下划线形式有效。  
  
 下面的示例生成 C4937：  
  
```  
// C4937.cpp  
// compile with: /openmp /W4  
#include "omp.h"  
int main() {  
   #pragma omp critical ( __leave )   // C4937  
   ;  
  
   // OK  
   #pragma omp critical ( leave )  
   ;  
}  
```
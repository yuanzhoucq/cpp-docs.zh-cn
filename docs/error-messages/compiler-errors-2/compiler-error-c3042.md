---
title: "编译器错误 C3042 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3042
dev_langs:
- C++
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: d6e26077e9ced646615681c1472661145939887a
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3042"></a>编译器错误 C3042
“copyprivate”和“nowait”子句不能同时出现在 OpenMP“directive”指令中  
  
 [Copyprivate](../../parallel/openmp/reference/copyprivate.md)和[nowait](../../parallel/openmp/reference/nowait.md)是互相排斥指定指令上的子句。 若要修复此错误，请删除 `copyprivate` 或 `nowait` 子句之一或两者一起删除。  
  
 以下示例生成 C3042：  
  
```  
// C3042.cpp  
// compile with: /openmp /c  
#include <stdio.h>  
#include "omp.h"  
  
double d;  
  
int main() {  
    #pragma omp parallel private(d)  
   {  
      #pragma omp single copyprivate(d) nowait   // C3042  
      {  
      }  
   }  
}  
```

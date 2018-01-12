---
title: "编译器错误 C3042 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3042
dev_langs: C++
helpviewer_keywords: C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15099fd212c58df0369749a497a277ecb7f6987e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3042"></a>编译器错误 C3042
“copyprivate”和“nowait”子句不能同时出现在 OpenMP“directive”指令中  
  
 [Copyprivate](../../parallel/openmp/reference/copyprivate.md) 和 [nowait](../../parallel/openmp/reference/nowait.md) 子句在指定的指令上彼此排斥。 若要修复此错误，请删除 `copyprivate` 或 `nowait` 子句之一或两者一起删除。  
  
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
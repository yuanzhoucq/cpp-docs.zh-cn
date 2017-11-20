---
title: "编译器错误 C3040 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3040
dev_langs: C++
helpviewer_keywords: C3040
ms.assetid: 29e857ac-74f0-4ec6-becf-9026e38c160e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7954c0904cd39ff5ab6e6698030aa701b3735e3f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3040"></a>编译器错误 C3040
“var”：“reduction”子句中的变量类型与 reduction 运算符“operator”不兼容  
  
 [reduction](../../parallel/openmp/reference/reduction.md) 子句中的变量不能与 reduction 运算符一起使用。  
  
 下面的示例生成 C3040：  
  
```  
// C3040.cpp  
// compile with: /openmp /c  
#include "omp.h"  
double d;  
  
int main() {  
   #pragma omp parallel reduction(&:d)   // C3040  
      ;  
  
   #pragma omp parallel reduction(-:d)  // OK  
      ;  
}  
```
---
title: "编译器错误 C3035 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3035
dev_langs: C++
helpviewer_keywords: C3035
ms.assetid: af34fad2-2b45-42d0-a9ff-04eab3e91c37
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 820a09741508c710d851182d9e1a02489c1ed2ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3035"></a>编译器错误 C3035
OpenMP“ordered”指令必须使用“ordered”子句直接绑定到“for”或“parallel for”指令  
  
 ordered 子句的格式不正确。  
  
 下面的示例生成 C3035：  
  
```  
// C3035.cpp  
// compile with: /openmp /link vcomps.lib  
int main() {  
   int n = 0, x, i;  
  
   #pragma omp parallel private(n)  
   {  
      #pragma omp ordered   // C3035  
      // Try the following line instead:  
      // #pragma omp for ordered  
       for (i = 0 ; i < 10 ; ++i)  
         ;  
   }  
}  
```
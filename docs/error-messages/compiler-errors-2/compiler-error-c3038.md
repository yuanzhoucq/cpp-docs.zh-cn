---
title: "编译器错误 C3038 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3038
dev_langs:
- C++
helpviewer_keywords:
- C3038
ms.assetid: 140ada3e-5636-43ef-a4ee-22a9f66a771f
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 3ddd3aaface0e500dc92778333cd3672398909da
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3038"></a>编译器错误 C3038
“var”：“private”子句中的变量不能是封闭上下文中的 reduction 变量  
  
 并行指令的 [reduction](../../parallel/openmp/reference/reduction.md) 子句中出现的变量不能在 [private](../../parallel/openmp/reference/private-openmp.md) 子句中指定，后者位于绑定到并行构造的工作共享指令上。  
  
 下面的示例生成 C3038：  
  
```  
// C3038.cpp  
// compile with: /openmp /c  
int g_i, g_i2;  
  
int main() {  
   int i;  
  
   #pragma omp parallel reduction(+: g_i)  
   {  
      #pragma omp for private(g_i)   // C3038  
      // try the following line instead  
      // #pragma omp for private(g_i2)  
      for (i = 0; i < 10; ++i)  
         g_i += i;  
   }  
}  
```

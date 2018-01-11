---
title: "编译器错误 C3053 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3053
dev_langs: C++
helpviewer_keywords: C3053
ms.assetid: ab9a25f3-e341-4f6e-8e69-069b4a963a64
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2cc685874a1c7b8b2f4ed8d4e49b0dd3ac899e67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3053"></a>编译器错误 C3053
“symbol”: “threadprivate”只对全局或静态数据项有效  
  
 传递给 [threadprivate](../../parallel/openmp/reference/threadprivate.md) 的符号必须是全局或静态的。  
  
 以下示例生成 C3053：  
  
```  
// C3053.cpp  
// compile with: /openmp  
void Test() {  
   int x, y;  
   #pragma omp threadprivate(x, y)   // C3053  
   #pragma omp parallel copyin(x, y)  
   {  
      x = y;  
   }  
}  
```  
  
 可能的解决方法：  
  
```  
// C3053b.cpp  
// compile with: /openmp /LD  
int x, y;  
#pragma omp threadprivate(x, y)  
  
void Test() {  
   #pragma omp parallel copyin(x, y)  
   {  
      x = y;  
   }  
}  
```
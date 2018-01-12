---
title: "编译器错误 C3033 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3033
dev_langs: C++
helpviewer_keywords: C3033
ms.assetid: 8628b6bb-a650-4ed2-af13-57acd2f7ddbb
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 18b9381f15af4d337abc89da1c82e22cfa6a14ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3033"></a>编译器错误 C3033
“var”: “clause”子句中的变量不能是常量限定类型  
  
 传递给某些子句的值不能为 `const` 变量。  
  
 下面的示例生成 C3033：  
  
```  
// C3033.cpp  
// compile with: /openmp /link vcomps.lib  
int main() {  
   const int val = 1;  
   int val2 = 1;  
  
   #pragma omp parallel reduction(+ : val)   // C3033  
   ;  
  
   #pragma omp parallel reduction(+ : val2)   // OK  
   ;  
}  
```
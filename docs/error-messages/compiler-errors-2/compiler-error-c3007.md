---
title: 编译器错误 C3007 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3007
dev_langs:
- C++
helpviewer_keywords:
- C3007
ms.assetid: e415ef42-bdc9-4f32-8198-5e25b289a089
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1424683db17247c6e31d0d26bce31f420353968
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33262385"
---
# <a name="compiler-error-c3007"></a>编译器错误 C3007
“arg”: OpenMP“directive”指令上的子句没有采用参数  
  
 OpenMP 指令具有一个参数，但没有采用参数。  
  
 以下示例生成 C3007：  
  
```  
// C3007.c  
// compile with: /openmp  
int main()  
{  
   #pragma omp parallel for ordered(2)   // C3007  
}  
```
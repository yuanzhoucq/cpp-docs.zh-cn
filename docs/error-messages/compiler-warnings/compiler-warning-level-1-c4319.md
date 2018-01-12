---
title: "编译器警告 （等级 1） C4319 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4319
dev_langs: C++
helpviewer_keywords: C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b7008b0f618048f5a4538a7aff55f03bab3d406d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4319"></a>编译器警告（等级 1）C4319
“operator”：将“type”零扩展到更大的“type”  
  
 ~（按位求补）运算符的结果无符号，然后在转换为更大的类型时进行零扩展。  
  
 在下面的示例中，~(a - 1) 按 32 位无符号 long 表达式进行计算，然后通过零扩展转换为 64 位。 这会导致意外的运算结果。  
  
```  
// C4319.cpp  
// compile with: cl /W4 C4319.cpp  
int main() {  
   unsigned long a = 0;  
   unsigned long long q = 42;  
   q = q & ~(a - 1);    // C4319 expected  
}  
```
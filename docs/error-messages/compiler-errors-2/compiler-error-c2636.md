---
title: 编译器错误 C2636 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2636
dev_langs:
- C++
helpviewer_keywords:
- C2636
ms.assetid: 379873ec-8d05-49f8-adf1-b067bc07bdb8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61422fcf03cabd6d7c2ed8bca23b9170df7e52bc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2636"></a>编译器错误 C2636
identifier： 指向引用成员的指针是非法的  
  
 未声明指向引用成员的指针。  
  
 下面的示例生成 C2636:  
  
```  
// C2636.cpp  
struct S {};  
int main() {  
   int &S::*prs;   // C2636  
   int S::*prs1;   // OK  
   int *S::*prs2;   // OK  
}  
```
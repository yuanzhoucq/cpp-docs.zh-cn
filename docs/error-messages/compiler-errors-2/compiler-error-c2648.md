---
title: "编译器错误 C2648 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2648
dev_langs:
- C++
helpviewer_keywords:
- C2648
ms.assetid: ce338337-9154-4f85-bb61-b05fdbfad75d
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 99d52f3c07c0c20e49fa46baeba4cde618e286c7
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2648"></a>编译器错误 C2648
identifier： 使用的成员，因为默认参数需要静态成员  
  
 作为默认参数使用了非静态成员。  
  
 下面的示例生成 C2648:  
  
```  
// C2648.cpp  
// compile with: /c  
class C {  
public:  
   int i;  
   static int j;  
   void func1( int i = i );  // C2648  i is not static  
   void func2( int i = j );  // OK  
};  
```

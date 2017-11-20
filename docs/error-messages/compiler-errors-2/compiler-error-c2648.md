---
title: "编译器错误 C2648 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2648
dev_langs: C++
helpviewer_keywords: C2648
ms.assetid: ce338337-9154-4f85-bb61-b05fdbfad75d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 99d52f3c07c0c20e49fa46baeba4cde618e286c7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
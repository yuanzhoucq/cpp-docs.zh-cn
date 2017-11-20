---
title: "编译器错误 C2250 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2250
dev_langs: C++
helpviewer_keywords: C2250
ms.assetid: f990986f-5c7d-4af4-a25c-b35540f1e217
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8a0d72b1bc986ec9ca3a2be5ffa0454cabad0def
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2250"></a>编译器错误 C2250
identifier： 不明确的 class::member 继承  
  
 派生的类继承的虚函数的虚拟基类的多个重写。 这些替代是在派生类中不明确。  
  
 下面的示例生成 C2286：  
  
```  
// C2250.cpp  
// compile with: /c  
// C2250 expected  
struct V {  
   virtual void vf();  
};  
  
struct A : virtual V {  
   void vf();  
};  
  
struct B : virtual V {  
   void vf();  
};  
  
struct D : A, B {  
   // Uncomment the following line to resolve.  
   // void vf();  
};  
```
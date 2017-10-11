---
title: "编译器错误 C2931 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2931
dev_langs:
- C++
helpviewer_keywords:
- C2931
ms.assetid: 33430407-b149-4ba3-baf8-b0dae1ea3a5d
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 8b8289508c84b24a5077be2160a7915900d3619a
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2931"></a>编译器错误 C2931
“class”: type-class-id 重新定义为“identifier”的成员函数  
  
 不能使用泛型或模板类作为另一个类的成员函数。  
  
 如果大括号匹配不正确，则可能导致此错误。  
  
 下面的示例生成 C2931：  
  
```  
// C2931.cpp  
// compile with: /c  
template<class T>   
struct TC { };   
struct MyStruct {  
   void TC<int>();   // C2931  
};  
  
struct TC2 { };   
struct MyStruct2 {  
   void TC2();  
};  
```  
  
 使用泛型时也可能发生 C2931：  
  
```  
// C2931b.cpp  
// compile with: /clr /c  
generic<class T> ref struct GC {};  
struct MyStruct {  
   void GC<int>();   // C2931  
   void GC2();   // OK  
};  
```

---
title: "编译器错误 C2801 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2801
dev_langs:
- C++
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 41e7956ace6c54cd55a2ed9f68f18c867bc80ad9
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2801"></a>编译器错误 C2801
operator operator 必须为非静态成员  
  
 以下运算符可以进行重载仅作为非静态成员：  
  
-   分配`=`  
  
-   类成员访问`->`  
  
-   下标`[]`  
  
-   函数调用`()`  
  
 C2801 的可能原因：  
  
-   重载的运算符不是类、 结构或联合成员。  
  
-   重载的运算符被声明`static`。  
  
-   下面的示例生成 C2801:  
  
```  
// C2801.cpp  
// compile with: /c  
operator[]();   // C2801 not a member  
class A {  
   static operator->();   // C2801 static  
   operator()();   // OK  
};  
```

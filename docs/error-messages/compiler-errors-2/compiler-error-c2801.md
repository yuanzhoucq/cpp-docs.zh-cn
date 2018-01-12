---
title: "编译器错误 C2801 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2801
dev_langs: C++
helpviewer_keywords: C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bbdbfdc1b7bb9445b1a709afb42944eea0d7f241
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
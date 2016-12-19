---
title: "编译器错误 C2801 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2801"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2801"
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2801
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator operator”必须是非静态成员  
  
 下列运算符只能重载为非静态成员：  
  
-   赋值 `=`  
  
-   类成员访问 `->`  
  
-   下标 `[]`  
  
-   函数调用 `()`  
  
 C2801 的可能原因：  
  
-   重载运算符不是类、结构或联合的成员。  
  
-   重载运算符被声明为 `static`。  
  
-   下面的示例生成 C2801：  
  
```  
// C2801.cpp  
// compile with: /c  
operator[]();   // C2801 not a member  
class A {  
   static operator->();   // C2801 static  
   operator()();   // OK  
};  
```
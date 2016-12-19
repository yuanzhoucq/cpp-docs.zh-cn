---
title: "编译器错误 C2758 | Microsoft Docs"
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
  - "C2758"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2758"
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2758
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”：必须初始化引用类型的成员  
  
 如果构造函数未初始化初始值设定项列表中引用类型的成员，则会导致编译器错误 C2758。  编译器将该成员保留为未定义状态。  如果已在构造函数的初始化列表中声明引用成员变量或为其赋值，则必须对其进行初始化。  
  
 下面的示例生成 C2758：  
  
```  
// C2758.cpp  
// Compile by using: cl /W3 /c C2758.cpp  
struct A {  
   const int i;  
  
   A(int n) { };   // C2758  
   // try the following line instead  
   // A(int n) : i{n} {};  
};  
```
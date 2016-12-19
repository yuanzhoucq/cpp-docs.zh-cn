---
title: "__super | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__super_cpp"
  - "__super"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__super 关键字 [C++]"
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __super
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 允许您显式说明要为正在重写的函数调用基类实现。  
  
## 语法  
  
```  
  
__super::  
member_function  
();  
  
```  
  
## 备注  
 在重载决策阶段将考虑所有可访问的基类方法，可提供最佳匹配项的函数就是调用的函数。  
  
 `__super` 只能在成员函数体内显示。  
  
 `__super` 不能与声明一起使用。  有关更多信息，请参见[using 声明](../cpp/using-declaration.md)。  
  
 在引入插入代码的[特性](../windows/cpp-attributes-reference.md)后，您的代码可能包含一个或多个基类，您不知道该基类的名称，但其包含您希望调用的方法。  
  
## 示例  
  
```  
// deriv_super.cpp  
// compile with: /c  
struct B1 {  
   void mf(int) {}  
};  
  
struct B2 {  
   void mf(short) {}  
  
   void mf(char) {}  
};  
  
struct D : B1, B2 {  
   void mf(short) {  
      __super::mf(1);   // Calls B1::mf(int)  
      __super::mf('s');   // Calls B2::mf(char)  
   }  
};  
```  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)
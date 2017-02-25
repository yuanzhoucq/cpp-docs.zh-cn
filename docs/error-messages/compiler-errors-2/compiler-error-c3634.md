---
title: "编译器错误 C3634 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3634"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3634"
ms.assetid: fd09f10c-f863-483b-9756-71c16b760b02
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3634
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”：不能定义托管或 WinRT 类的抽象方法  
  
 可在托管或 WinRT 类中声明一个抽象方法，但不能定义它。  
  
 以下示例生成 C3634：  
  
```  
// C3634.cpp  
// compile with: /clr  
ref class C {  
   virtual void f() = 0;  
};  
  
void C::f() {   // C3634 - don't define managed class' pure virtual method  
}  
```  
  
 **C\+\+ 托管扩展**  
  
 以下示例生成 C3634：  
  
```  
// C3634b.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
  
__gc class C {  
   virtual void f() = 0;  
};  
  
void C::f() {   // C3634 - don't define managed class' pure virtual method  
}  
```
---
title: "编译器错误 C3648 | Microsoft Docs"
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
  - "C3648"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3648"
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3648
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此显式重写语法需要 \/clr:oldSyntax  
  
 当编译最新版本的托管语法时，编译器找到早期版本的显式重写语法。  
  
 有关更多信息，请参见[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。  有关早期语法的更多信息，请参见[显式重写](../../cpp/explicit-overrides-cpp.md)。  
  
 下面的示例生成 C3648：  
  
```  
// C3648.cpp  
// compile with: /clr  
public interface struct I {  
   void f();  
};  
  
public ref struct R : I {  
   virtual void I::f() {}   // C3648  
   // try the following line instead  
   // virtual void f() = I::f{}  
};  
```
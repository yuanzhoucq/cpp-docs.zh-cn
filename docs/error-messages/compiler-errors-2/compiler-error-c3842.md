---
title: "编译器错误 C3842 | Microsoft Docs"
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
  - "C3842"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3842"
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3842
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“函数”: 不支持在 WinRT 或托管类型的成员函数上使用“const”和“volatile”限定符  
  
 Windows 运行时或托管类型的成员函数上不支持 [const](../../cpp/const-cpp.md) 和 [volatile](../../cpp/volatile-cpp.md)。  
  
 下面的示例生成 C3842：  
  
```  
// C3842a.cpp  
// compile with: /clr /c  
public ref struct A {  
   void f() const {}   // C3842  
   void f() volatile {}   // C3842  
  
   void f() {}  
};  
  
```
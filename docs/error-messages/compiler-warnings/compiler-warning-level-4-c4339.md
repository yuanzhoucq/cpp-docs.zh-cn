---
title: "编译器警告（等级 4）C4339 | Microsoft Docs"
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
  - "C4339"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4339"
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4339
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 在 WinRT 或 CLR 元数据中检测到使用了未定义的类型 \- 使用此类型可能导致运行时异常  
  
 类型未在针对 Windows 运行时或公共语言运行时编译的代码中定义。  定义类型以避免可能的运行时异常。  
  
 默认情况下，此警告处于关闭状态。  请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)了解详细信息。  
  
 下面的示例将生成 C4339，并演示如何修复此错误：  
  
```  
// C4339.cpp  
// compile with: /W4 /clr /c  
// C4339 expected  
#pragma warning(default : 4339)  
  
// Delete the following line to resolve.  
class A;  
  
// Uncomment the following line to resolve.  
// class A{};  
  
class X {  
public:  
   X() {}  
  
   virtual A *mf() {  
      return 0;  
   }  
};  
  
X * f() {  
   return new X();  
}  
```
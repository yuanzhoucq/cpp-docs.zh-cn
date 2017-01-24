---
title: "Compiler Error C3252 | Microsoft Docs"
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
  - "C3252"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3252"
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C3252
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“method”：不能降低托管或 WinRT 类型中虚方法的可访问性  
  
 实现来自基类的虚方法或来自接口的任意方法的类不能减少该方法的访问。  
  
 请注意，接口中的所有方法都是公共的。  
  
 下列示例生成 C3252，并演示如何修复此错误：  
  
```  
// C3252.cpp  
// compile with: /clr /c  
ref class A {  
public:  
   virtual void f1() {}  
};  
  
ref class B : public A {  
// To fix, uncomment the following line:   
// public:      
   virtual void f1() override sealed {}   // C3252, make this method public  
};  
```
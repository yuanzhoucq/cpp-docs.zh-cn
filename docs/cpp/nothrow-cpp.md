---
title: "nothrow (C++) | Microsoft Docs"
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
  - "nothrow_cpp"
  - "nothrow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C++], nothrow"
  - "nothrow __declspec 关键字"
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# nothrow (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 `__declspec` 扩展特性，可在函数声明中使用。  
  
## 语法  
  
```  
  
return-type __declspec(nothrow) [call-convention] function-name ([argument-list])  
```  
  
## 备注  
 此特性告知编译器，声明的函数及其调用的函数从不引发异常。  利用当前默认的同步异常处理模式，编译器可以消除跟踪此类函数中的某些不可展开的对象的生命周期的机制，从而显著减小代码大小。  在使用以下预处理器指令的情况下，下面的三个函数声明是等效的：  
  
```  
#define WINAPI __declspec(nothrow) __stdcall   
  
void WINAPI f1();  
void __declspec(nothrow) __stdcall f2();  
void __stdcall f3() throw();  
```  
  
 使用 `void __declspec(nothrow) __stdcall f2();` 有一个好处，即，您可以使用 API 定义（如 `#define` 语句阐释的定义）在一组函数上轻松指定 `nothrow`。  第三个声明 `, void __stdcall f3() throw();` 是由 C\+\+ 标准定义的语法。  
  
 有关详细信息，请参阅[同步异常处理](http://msdn.microsoft.com/zh-cn/81595fae-d8ab-4c14-9670-8d6639cc0369)。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)
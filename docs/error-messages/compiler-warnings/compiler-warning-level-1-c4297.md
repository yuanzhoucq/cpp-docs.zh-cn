---
title: "编译器警告（等级 1）C4297 | Microsoft Docs"
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
  - "C4297"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4297"
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4297
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 假定函数不引发异常，但确实发生了异常  
  
 函数声明中包含一个`noexcept` 说明符（可能为隐式）、一个空 `throw` 异常说明符或一个 [\_\_declspec \(nothrow\)](../../cpp/nothrow-cpp.md) 特性，而定义包含一个或多个 [throw](../../cpp/try-throw-and-catch-statements-cpp.md) 语句。  若要解决 C4297，请不要尝试在声明了 `__declspec(nothrow)`、`noexcept(true)` 或 `throw()` 的函数中引发异常。  或者，删除 `noexcept`、`throw()` 或 `__declspec(nothrow)` 规范。  
  
 默认情况下，编译器为用户定义的析构函数和释放函数以及编译器生成的特殊成员函数生成隐式 `noexcept(true)` 说明符。  这符合 ISO C\+\+ 11 标准。  若要防止生成隐式 noexcept 说明符，并将编译器还原到 Visual Studio 2013 的非标准行为，请使用 **\/Zc:implicitNoexcept\-** 编译器选项。  有关详细信息，请参阅 [\/Zc:implicitNoexcept（隐式异常说明符）](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md)。  
  
 有关异常规范的详细信息，请参阅[异常规范 \(throw\)](../../cpp/exception-specifications-throw-cpp.md)。  此外，有关如何在编译时修改异常处理行为的信息，请参阅 [\/EH（异常处理模型）](../../build/reference/eh-exception-handling-model.md)。  
  
 还会为标记了外部“C”的 \_\_declspec\([dllexport](../../cpp/dllexport-dllimport.md)\) 函数（即使它们是 C\+\+ 函数）生成此警告。  
  
 下面的示例生成 C4297：  
  
```  
// C4297.cpp  
// compile with: /W1 /LD  
void __declspec(nothrow) f1()   // declared nothrow  
// try the following line instead  
// void f1()  
{  
   throw 1;   // C4297  
}  
```
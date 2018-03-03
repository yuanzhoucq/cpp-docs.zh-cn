---
title: "编译器警告 （等级 1） C4297 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4297
dev_langs:
- C++
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9253ae709109927e69940d5023b542dfb543c6de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4297"></a>编译器警告（等级 1）C4297
“function”: 假定函数不引发异常，但确实发生了异常  
  
 函数声明中包含的 （可能为隐式）`noexcept`说明符为一个空`throw`异常说明符或[__declspec （nothrow)](../../cpp/nothrow-cpp.md)属性，而定义包含一个或多个[引发](../../cpp/try-throw-and-catch-statements-cpp.md)语句。 若要解决 C4297，请不要尝试在声明了 `__declspec(nothrow)`、`noexcept(true)` 或 `throw()` 的函数中引发异常。 或者，删除 `noexcept`、`throw()` 或 `__declspec(nothrow)` 规范。  
  
 默认情况下，编译器为用户定义的析构函数和释放函数以及编译器生成的特殊成员函数生成隐式 `noexcept(true)` 说明符。 这符合 ISO C++ 11 标准。 若要防止生成隐式 noexcept 说明符，并还原到 Visual Studio 2013 的非标准行为编译器，请使用**/zc: implicitnoexcept-**编译器选项。 有关详细信息，请参阅[/zc: implicitnoexcept （隐式异常说明符）](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md)。  
  
 有关异常规范的详细信息，请参阅[异常规范 (throw)](../../cpp/exception-specifications-throw-cpp.md)。 另请参阅[/EH （异常处理模型）](../../build/reference/eh-exception-handling-model.md)有关如何修改异常处理在编译时的行为的信息。  
  
 __Declspec 也会生成此警告 ([dllexport](../../cpp/dllexport-dllimport.md)) 函数标记 extern"C"，即使它们是 c + + 函数。  
  
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
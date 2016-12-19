---
title: "__clrcall | Microsoft Docs"
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
  - "__clrcall"
  - "__clrcall_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__clrcall 关键字 [C++]"
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __clrcall
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 指定只能从托管代码调用的函数。对所有只能从托管代码调用的虚函数使用 `__clrcall`。  但是，此调用约定不能用于从本机代码调用的函数。  
  
 当通过指针从托管函数调用到虚拟托管函数或从托管函数调用到托管函数时，可使用 `__clrcall` 来提高性能。  
  
 入口点是编译器生成的单独函数。  如果函数同时具有本机和托管入口点，则其中一个将是具有函数实现的实际函数。  其他函数将是调用到实际函数的单独函数（形式转换 \(thunk\)）并允许公共语言运行时执行 PInvoke。  当将函数标记为 `__clrcall` 时，您可以指示函数实现必须是 MSIL，并且不生成本机入口点函数。  
  
 当采用本机函数的地址时，如果未指定 `__clrcall`，编译器将使用本机入口点。  `__clrcall` 指示函数为托管函数，并且不需要经历从托管到本机的转换。  在这种情况下，编译器将使用托管入口点。  
  
 当使用了 **\/clr**（不是 **\/clr:pure** 或 **\/clr:safe** ）而未使用 `__clrcall` 时，采用函数的地址将始终返回本机入口点函数的地址。  当使用了 `__clrcall` 时，不会创建本机入口点函数，因此您将获得托管函数的地址，而不是入口点形式转换 \(thunk\) 函数的地址。  有关详细信息，请参阅[双重形式转换](../dotnet/double-thunking-cpp.md)。  
  
 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md) 表示所有函数和函数指针都是 `__clrcall`，且编译器不允许将编译单位中的函数标记为 `__clrcall` 之外的任何内容。  当使用 **\/clr:pure** 时，`__clrcall` 只能在函数指针和外部声明上指定。  
  
 可以直接从使用 **\/clr** 编译的现有 C\+\+ 代码调用 `__clrcall` 函数（只要该函数具有 MSIL 实现）。  例如，`__clrcall` 函数无法直接从具有内联 asm 的函数调用，且无法调用特定于 CPU 的内部函数，即使这些函数是使用 **\/clr** 编译的。  
  
 `__clrcall` 函数指针仅能在创建它们的应用程序域中使用。不要跨应用程序域传递 <xref:System.CrossAppDomainDelegate> 函数指针，而应使用 `__clrcall`。  有关详细信息，请参阅[应用程序域和 Visual C\+\+](../dotnet/application-domains-and-visual-cpp.md)。  
  
## 示例  
  
```  
// clrcall.cpp  
// compile with: /clr:oldSyntax /LD  
void __clrcall Test1( ) {}  
void (__clrcall *fpTest1)( ) = &Test1;  
```  
  
## 示例  
 请注意，当使用 `__clrcall` 声明函数时，将根据需要生成代码；例如，当调用函数时。  
  
```  
// clrcall2.cpp  
// compile with: /clr  
using namespace System;  
int __clrcall Func1() {  
   Console::WriteLine("in Func1");  
   return 0;  
}  
  
// Func1 hasn't been used at this point (code has not been generated),   
// so runtime returns the adddress of a stub to the function  
int (__clrcall *pf)() = &Func1;  
  
// code calls the function, code generated at difference address  
int i = pf();   // comment this line and comparison will pass  
  
int main() {  
   if (&Func1 == pf)  
      Console::WriteLine("&Func1 == pf, comparison succeeds");  
   else   
      Console::WriteLine("&Func1 != pf, comparison fails");  
  
   // even though comparison fails, stub and function call are correct  
   pf();  
   Func1();  
}  
```  
  
  **in Func1**  
**&Func1 \!\= pf, comparison fails**  
**in Func1**  
**in Func1**   
## 示例  
 以下示例显示，您可以定义函数指针以便将该函数指针声明为仅从托管代码调用。  这样，编译器便能直接调用托管函数并避免本机入口点（双形式转换 \(thunk\) 问题）。  
  
```  
// clrcall3.cpp  
// compile with: /clr  
void Test() {  
   System::Console::WriteLine("in Test");  
}  
  
int main() {  
   void (*pTest)() = &Test;  
   (*pTest)();  
  
   void (__clrcall *pTest2)() = &Test;  
   (*pTest2)();  
}  
```  
  
## 请参阅  
 [参数传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)
---
title: "__thiscall | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__thiscall"
  - "__thiscall_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__thiscall 关键字 [C++]"
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# __thiscall
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 `__thiscall` 调用预定用于成员函数,且是 C\+\+ 成员函数的默认调用约定,不使用可变参数。  在 `__thiscall`下，被调用方清理堆栈，对于 `vararg` 功能是不可能的。  参数从右向左被推入堆栈，与此同时，`this` 指针通过寄存器 ECX 传递到 x86 结构上而不是堆栈上。  
  
 一个原因使用 `__thiscall` 是在默认情况下成员函数使用 `__clrcall` 的类。  在这种情况下，可以使用 `__thiscall` 使本机代码中的单个成员函数可调用。  
  
 当使用 [\/clr:pure](../build/reference/clr-common-language-runtime-compilation.md) 编译时，除非有指定值，否则所有函数和函数指针均为 `__clrcall`。  
  
 在 Visual C\+\+ 2005 之前的版本中，因为 `thiscall` 不是关键字，程序中无法显式指定 thiscall 调用的约定。  
  
 `vararg` 成员函数使用 `__cdecl` 调用约定。  所有函数参数被推送到堆栈上，`this` 指针被放置在堆栈的最后。  
  
 由于此调用仅适用于 C\+\+，因此不存在 C 名称修饰模式。  
  
 在ARM及其[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 设备上, `__thiscall` 由编译器接受及忽略.  
  
 对于非静态函数类，如果函数是超行定义的，则调用约定修饰符不必在超行定义中指定。  用于非静态成员方法类，也就是说，假定声明时具有的泛型是指定的调用约定。  
  
## 示例  
  
```  
// thiscall_cc.cpp  
// compile with: /c /clr:oldSyntax  
struct CMyClass {  
   void __thiscall mymethod();  
   void __clrcall mymethod2();  
};  
```  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [参数传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)
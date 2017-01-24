---
title: "如何：迁移到 /clr:safe (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 编译器选项 [C++], 迁移到 /clr:safe"
  - "迁移 [C++], 可验证程序集"
  - "升级 Visual C++ 应用程序, 可验证程序集"
  - "可验证程序集 [C++], 迁移到"
ms.assetid: 75f9aae9-1dcc-448a-aa11-2d96f972f9d2
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：迁移到 /clr:safe (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 可以使用 **\/clr:safe** 生成可验证的组件，这将使编译器针对每个不可验证的代码构造生成错误。  
  
## 备注  
 以下问题将生成可验证性错误：  
  
-   本机类型。  即使不使用本机类型，本机类、结构、指针或数组的声明也将阻止编译。  
  
-   全局变量  
  
-   对任何非托管库的函数调用，包括公共语言运行时函数调用  
  
-   可验证函数不能包含用于向下强制转换的 [static\_cast 运算符](../cpp/static-cast-operator.md)。  [static\_cast 运算符](../cpp/static-cast-operator.md) 可用于在基元类型之间进行强制转换，但对于向下强制转换，必须使用 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md) 或 C 样式强制转换（作为 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md) 实现）。  
  
-   可验证函数不能包含 [reinterpret\_cast 运算符](../cpp/reinterpret-cast-operator.md)（或任何等效的 C 样式强制转换）。  
  
-   可验证函数不能对 [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md) 执行算术运算。  它只能够分配给它和取消对它的引用。  
  
-   可验证函数只能引发或捕捉指向引用类型的指针，因此在引发前必须将值类型装箱。  
  
-   可验证函数只能调用可验证函数（因此不允许调用公共语言运行时，包括 `AtEntry`\/`AtExit`，并且因此不允许使用全局构造函数）。  
  
-   可验证类不能使用 <xref:System.Runtime.InteropServices.LayoutKind>。  
  
-   如果生成 EXE，则主函数不能声明任何参数，因此必须使用 <xref:System.Environment.GetCommandLineArgs%2A> 检索命令行变量。  
  
-   对虚函数进行非虚拟调用。  例如：  
  
    ```  
    // not_verifiable.cpp  
    // compile with: /clr  
    ref struct A {  
       virtual void Test() {}  
    };  
  
    ref struct B : A {};  
  
    int main() {  
       B^ b1 = gcnew B;  
       b1->A::Test();   // Non-virtual call to virtual function  
    }  
    ```  
  
 同样，在可验证代码中不能使用下面的关键字：  
  
-   [unmanaged](../preprocessor/managed-unmanaged.md) 和 [pack](../preprocessor/pack.md) 杂注  
  
-   [naked](../cpp/naked-cpp.md) 和 [align](../cpp/align-cpp.md) [\_\_declspec](../cpp/declspec.md) 修饰符  
  
-   [\_\_asm](../assembler/inline/asm.md)  
  
-   [\_\_based](../cpp/based-grammar.md)  
  
-   [\_\_try](../cpp/try-except-statement.md) 和 `__except`  
  
## 请参阅  
 [纯代码和可验证代码](../dotnet/pure-and-verifiable-code-cpp-cli.md)
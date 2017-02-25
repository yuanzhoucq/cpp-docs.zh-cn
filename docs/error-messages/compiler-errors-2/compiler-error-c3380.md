---
title: "编译器错误 C3380 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3380"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3380"
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C3380
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: 程序集访问说明符无效 \- 只允许“public”或“private”  
  
 应用于托管类或结构时，[public](../../cpp/public-cpp.md) 和 [private](../../cpp/private-cpp.md) 关键字指示是否通过程序集元数据公开此类。 程序中使用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 编译的类只可使用 `public` 或 `private`。  
  
 当与 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 一起使用时，`ref` 和 `value` 关键字指示该类受托管（请参阅[类和结构 \(托管\)](../../windows/classes-and-structs-cpp-component-extensions.md)）。  
  
 以下示例生成 C3380：  
  
```  
// C3380_2.cpp // compile with: /clr protected ref class A {   // C3380 // try the following line instead // ref class A { public: static int i = 9; }; int main() { A^ myA = gcnew A; System::Console::WriteLine(myA->i); }  
```  
  
 以下示例生成 C3380：  
  
```  
// C3380.cpp // compile with: /clr:oldSyntax #using <mscorlib.dll> protected __gc class A {   // C3380 // try the following line instead // __gc class A { public: static int i = 9; }; int main() { A *myA = new A; Console::WriteLine(myA->i); }  
```
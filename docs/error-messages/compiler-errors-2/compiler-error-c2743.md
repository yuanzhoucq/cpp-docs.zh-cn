---
title: "编译器错误 C2743 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2743"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2743"
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2743
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 无法捕获具有 \_\_clrcall 析构函数或复制构造函数的本机类型  
  
 用 **\/clr**（而不是 **\/clr:pure**）编译的模块尝试捕获本机类型的异常，其中该类型的析构函数或复制构造函数使用 \_`_clrcall` 调用约定。  
  
 当使用 **\/clr**（不是 **\/clr:pure**）编译时，异常处理要求本机类型中的成员函数应是 [\_\_cdecl](../../cpp/cdecl.md) 而不是 [\_\_clrcall](../../cpp/clrcall.md)。  在用 **\/clr** 编译的模块中，无法捕获具有使用 `__clrcall` 调用约定的成员函数的本机类型。  
  
 有关详细信息，请参阅[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 示例  
 下面的示例生成 C2743。  
  
```  
// C2743.cpp  
// compile with: /clr  
public struct S {  
   __clrcall ~S() {}  
};  
  
public struct T {  
   ~T() {}  
};  
  
int main() {  
   try {}  
   catch(S) {}   // C2743  
   // try the following line instead  
   // catch(T) {}  
  
   try {}  
   catch(S*) {}   // OK  
}  
```
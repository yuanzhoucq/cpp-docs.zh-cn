---
title: "编译器警告（等级 1）C4382 | Microsoft Docs"
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
  - "C4382"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4382"
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4382
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

引发“type”: 带有 \_\_clrcall 析构函数或复制构造函数的类型只能在 \/clr:pure 模块中捕获  
  
 当使用 **\/clr**（不是 **\/clr:pure**）编译时，异常处理要求本机类型中的成员函数应是 [\_\_cdecl](../../cpp/cdecl.md) 而不是 [\_\_clrcall](../../cpp/clrcall.md)。  在用 **\/clr** 编译的模块中，无法捕获具有使用 `__clrcall` 调用约定的成员函数的本机类型。  
  
 如果异常是在用 **\/clr:pure** 编译的模块中捕获的，则可以忽略此警告。  
  
 有关详细信息，请参阅[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 示例  
 下面的示例生成 C4382。  
  
```  
// C4382.cpp  
// compile with: /clr /W1 /c  
struct S {  
   __clrcall ~S() {}  
};  
  
struct T {  
   ~T() {}  
};  
  
int main() {  
   S s;  
   throw s;   // C4382  
  
   S * ps = &s;  
   throw ps;   // OK  
  
   T t;  
   throw t;   // OK  
}  
```
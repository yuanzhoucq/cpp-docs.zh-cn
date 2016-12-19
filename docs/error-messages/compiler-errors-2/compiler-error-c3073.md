---
title: "编译器错误 C3073 | Microsoft Docs"
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
  - "C3073"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3073"
ms.assetid: b24b9b8b-f9fb-4c3c-a1a0-97fad2081bfc
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3073
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: ref 类没有用户定义的复制构造函数  
  
 在 [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md) 编译中，编译器将不会为引用类型生成复制构造函数。  在任何 **\/clr** 编译中，如果希望复制类型的实例，则必须为引用类型定义自己的复制构造函数。  
  
 有关详细信息，请参阅[参考类型的 C\+\+ 堆栈语义](../../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
## 示例  
 下面的示例生成 C3073。  
  
```  
// C3073.cpp  
// compile with: /clr  
ref class R {  
public:  
   R(int) {}  
};  
  
ref class S {  
public:  
   S(int) {}  
   S(const S %rhs) {}   // copy constructor  
};  
  
void f(R) {}  
void f2(S) {}  
void f3(R%){}  
  
int main() {  
   R r(1);  
   f(r);   // C3073  
   f3(r);   // OK  
  
   S s(1);  
   f2(s);   // OK  
}  
```
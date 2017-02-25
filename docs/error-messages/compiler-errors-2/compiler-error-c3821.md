---
title: "编译器错误 C3821 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3821"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3821"
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器错误 C3821
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 托管类型或托管函数不能用在非托管函数中  
  
 具有内联程序集或 [setjmp](../../c-runtime-library/reference/setjmp.md) 的函数不能包含值类型或托管类。  要修复此错误，请移除内联程序集和 `setjmp`，或者移除托管对象。  
  
 如果尝试使用 vararg 函数中的自动存储，也将发生 C3821。有关更多信息，请参见[变量参数列表 \(...\) \(C\+\+\/CLI\)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)和[参考类型的 C\+\+ 堆栈语义](../../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
## 示例  
 下面的示例生成 C3821。  
  
```  
// C3821a.cpp  
// compile with: /clr /c  
public ref struct R {};  
void test1(...) {  
   R r;   // C3821  
}  
```  
  
## 示例  
 下面的示例生成 C3821。  
  
```  
// C3821b.cpp  
// compile with: /clr  
// processor: /x86  
ref class A {  
   public:  
   int i;  
};  
  
int main() {  
   // cannot use managed classes in this function  
   A ^a;     
  
   __asm {  
      nop  
   }  
} // C3821  
```  
  
## 示例  
 下面的示例生成 C3821。  
  
```  
// C3821c.cpp  
// compile with: /clr:oldSyntax  
// processor: /x86  
__gc  class A {  
   public:  
   int i;  
};  
  
int main() {  
   // cannot use managed classes in this function  
   A *a;     
  
   __asm {  
      nop  
   }  
} // C3821  
```
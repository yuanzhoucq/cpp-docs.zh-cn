---
title: "编译器错误 C3149 | Microsoft Docs"
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
  - "C3149"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3149"
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3149
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 此处没有顶级“char”，不能使用此类型  
  
 没有正确地指定声明。  
  
 例如，您可能定义了一个全局范围的 CLR 类型，并尝试在定义中创建该类型的一个变量。  由于不允许使用 CLR 类型的全局变量，所以编译器将生成 C3149。  
  
 若要解决此错误，请在函数或类型定义内声明 CLR 类型的变量。  
  
 下面的示例生成 C3149：  
  
```  
// C3149.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   // declare an array of value types   
   array< Int32 ^> IntArray;   // C3149  
   array< Int32>^ IntArray2;   // OK  
}  
```  
  
 下面的示例生成 C3149：  
  
```  
// C3149b.cpp  
// compile with: /clr /c  
delegate int MyDelegate(const int, int);  
void Test1(MyDelegate m) {}   // C3149  
void Test2(MyDelegate ^ m) {}   // OK  
```  
  
 **C\+\+ 托管扩展**  
  
 没有正确地使用托管对象。  
  
 下面的示例生成 C3149：  
  
```  
// C3149c.cpp  
// compile with: /clr:oldSyntax  
__gc class A {};  
  
int main() {  
   A a = new A;   // C3149  
   A *a = new A;   // OK  
}  
```
---
title: "编译器警告（等级 1）C4383 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4383"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4383"
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4383
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“instance\_dereference\_operator”: 当存在用户定义的“operator”运算符时，取消句柄引用的意义可以更改；请将该运算符编写为与操作数有关的显式静态函数  
  
 添加托管类型中取消引用运算符的用户定义的实例重写时，可以重写该类型的取消引用运算符的能力以返回该句柄的对象。  考虑编写一个静态的、用户定义的取消引用运算符。  
  
 有关更多信息，请参见[对象句柄运算符 \(^\)](../../windows/handle-to-object-operator-hat-cpp-component-extensions.md)和[% \(跟踪引用\)](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
 此外，其他语言编译器也无法通过引用的元数据使用实例运算符。  有关详细信息，请参阅[用户定义的运算符](../../dotnet/user-defined-operators-cpp-cli.md)。  
  
## 示例  
 下面的示例生成 C4383。  
  
```  
// C4383.cpp  
// compile with: /clr /W1  
  
ref struct S {  
   int operator*() { return 0; }   // C4383  
};  
  
ref struct T {  
   static int operator*(T%) { return 0; }  
};   
  
int main() {  
   S s;  
   S^ pS = %s;  
  
   T t;  
   T^ pT = %t;  
   T% rT = *pT;  
}  
```
---
title: "编译器警告（等级 1）C4350 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4350"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4350"
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4350
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

行为更改: 调用了“member1”而不是“member2”  
  
 rvalue 不能绑定到非常量引用。  在以前版本的 Visual C\+\+ 中，直接初始化时有可能将 rvalue 绑定到非常量引用。  现在，此代码将给出警告。  
  
 对于向后兼容性，仍然有可能将 rvalues 绑定到非常量引用，但仍然尽可能首选标准转换。  
  
 此警告表示 Visual C\+\+ .NET 2002 编译器行为的更改。  如果启用，对于正确代码可能给出此警告。  例如，使用 **std::auto\_ptr** 类模板时可能给出此警告。  
  
 如果收到此警告，请检查代码，以查看代码是否依赖于 rvalues 到非常量引用的绑定。  将常量添加到引用或提供附加的常量引用重载可能会解决该问题。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的示例生成 C4350：  
  
```  
// C4350.cpp  
// compile with: /W1  
#pragma warning (default : 4350)  
class A {};  
  
class B  
{  
public:  
   B(B&){}  
   // try the following instead  
   // B(const B&){}  
  
   B(A){}  
   operator A(){ return A();}  
};  
  
B source() { return A(); }  
  
int main()  
{  
   B ap(source());   // C4350  
}  
```
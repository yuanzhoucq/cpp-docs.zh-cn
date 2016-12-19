---
title: "参考类型的 C++ 堆栈语义 | Microsoft Docs"
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
  - "引用类型, C++ 堆栈语义"
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 参考类型的 C++ 堆栈语义
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Visual C\+\+ 2005 之前，引用类型的实例只能用`new` 运算符来创建，对象被创建在垃圾回收堆上。  但是现在，您可以用相同的语法，在栈上创建本机的引用类型实例。  因此，您无需使用 [gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md) 创建引用类型的对象。  此外，当对象超出范围时，编译器调用对象的析构函数。  
  
## 备注  
 当您使用堆栈语义创建引用类型实例时，编译器会在垃圾回收堆上内部地创建实例。 \(使用 `gcnew`\)。  
  
 当函数的签名或返回类型包括一个按值引用的类型的实例时，则函数会因为需要特殊处理而被标记（使用modreq）。  此特殊处理当前仅由 Visual C\+\+ 客户端提供；其他语言当前不支持用堆栈语义创建出来的引用类型的函数或数据。  
  
 其中一个使用`gcnew` （动态分配）堆栈语义的原因是，某些类型可能没有析构函数。  此外，如果在函数签名中使用堆栈语义来创建引用类型，无法让您的函数在除Visual C\+\+ 之外的语言上使用。  
  
 编译器将不会为引用类型生成复制构造函数。  因此，如果在签名中定义的函数使用了按值引用的类型，您必须为引用类型定义一个复制构造函数。  引用类型的复制构造函数具有以下形式的签名：`R(R%){}`。  
  
 编译器不会为引用类型生成默认的赋值运算符。  赋值运算符允许您用堆栈语义创建一个对象，并且其可以由现有的由堆栈语义创建出的对象初始化。  引用类型的赋值运算符都有以下形式的签名：`void operator=( R% ){}`。  
  
 如果类型的析构函数释放重要资源和使用堆栈语义的引用类型时，不需要显式调用析构函数 \(或调用 `delete`。\)  有关引用在类型的析构函数的详细信息，请参见 [Visual C\+\+ 中的析构函数和终结器](../misc/destructors-and-finalizers-in-visual-cpp.md)。  
  
 编译器生成的赋值运算符将遵循标准 C\+\+规范与以下这些额外规定：  
  
-   任何类型为句柄引用类型的非静态数据成员都是被浅表复制（与对待指针类型的非静态数据成员一样）。  
  
-   任何类型是值类型的非静态数据成员都将被浅表复制。  
  
-   任何类型为引用类型的实例的非静态数据成员将调用引用类型的复制构造函数。  
  
 编译器还提供 `%` 一元运算符用于将使用堆栈语义创建的引用类型的实例变为其基础句柄类型。  
  
 堆栈语义不可用于以下的引用类型：  
  
-   [委托](../windows/delegate-cpp-component-extensions.md)  
  
-   [数组](../windows/arrays-cpp-component-extensions.md)  
  
-   <xref:System.String>  
  
## 示例  
  
### 说明  
 下面的代码示例展示了如何用堆栈语义声明一个引用类型的实例，赋值运算符函数和复制构造函数如何工作，以及如何使用现有的堆栈语义创建的引用类型来初始化跟踪引用。  
  
### 代码  
  
```  
// stack_semantics_for_reference_types.cpp  
// compile with: /clr  
ref class R {  
public:  
   int i;  
   R(){}  
  
   // assignment operator  
   void operator=(R% r) {  
      i = r.i;  
   }  
  
   // copy constructor  
   R(R% r) : i(r.i) {}  
};  
  
void Test(R r) {}   // requires copy constructor  
  
int main() {  
   R r1;  
   r1.i = 98;  
  
   R r2(r1);   // requires copy constructor  
   System::Console::WriteLine(r1.i);  
   System::Console::WriteLine(r2.i);  
  
   // use % unary operator to convert instance using stack semantics  
   // to its underlying handle  
   R ^ r3 = %r1;  
   System::Console::WriteLine(r3->i);  
  
   Test(r1);  
  
   R r4;  
   R r5;  
   r5.i = 13;  
   r4 = r5;   // requires a user-defined assignment operator  
   System::Console::WriteLine(r4.i);  
  
   // initialize tracking reference  
   R % r6 = r4;  
   System::Console::WriteLine(r6.i);  
}  
```  
  
### Output  
  
```  
98  
98  
98  
13  
13  
```  
  
## 请参阅  
 [类和结构 \(托管\)](../windows/classes-and-structs-cpp-component-extensions.md)
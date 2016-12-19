---
title: "摘要 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "abstract"
  - "abstract_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "抽象关键字 [C++]"
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 摘要 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`abstract` 关键字声明以下两者之一：  
  
-   类型可被用作基类型，但其自身无法进行实例化。  
  
-   只可在派生类型中定义类型成员函数。  
  
## 所有平台  
 **语法**  
  
```  
  
class-declaration class-identifier abstract {}  
virtual return-type member-function-identifier() abstract ;  
  
```  
  
 **备注**  
  
 第一个示例语法将类声明为抽象类。  如果指定了 **\/ZW** 或 **\/clr** 编译器选项，则*类声明*组件可以是本机 C\+\+ 声明（`class` 或 `struct`），也可以是 C\+\+ 扩展声明（`ref class` 或 `ref struct`）。  
  
 第二个示例语法将虚拟成员函数声明为抽象函数。  将函数声明为抽象函数等同于将其声明为纯虚拟函数。  将成员函数声明为抽象函数也会导致封闭类声明为抽象类。  
  
 `abstract` 关键字在本机和平台特定的代码中受支持；也就是说，编译它时可选择性地使用 **\/ZW** 或 **\/clr** 编译器选项。  
  
 可在编译时检测类型是否为具有 `__is_abstract(``type``)` 类型特征的抽象类型。  有关详细信息，请参阅[编译器使用类型特征支持](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 `abstract` 关键字是上下文相关的重写说明符。  有关上下文相关关键字的详细信息，请参阅[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  有关重写说明符的详细信息，请参阅[如何：在本机编译中声明重写说明符](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 有关详细信息，请参阅 [Ref 类和结构](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx)。  
  
### 要求  
 编译器选项：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 下面的代码示例生成一个错误，因为类 `X` 被标记为 `abstract`。  
  
```  
// abstract_keyword.cpp  
// compile with: /clr  
ref class X abstract {  
public:  
   virtual void f() {}  
};  
  
int main() {  
   X ^ MyX = gcnew X;   // C3622  
}  
```  
  
 **示例**  
  
 下面的代码示例生成一个错误，因为它实例化被标记为 `abstract` 的本机类。  无论是否使用 **\/clr** 编译器选项，都将出现此错误。  
  
```  
// abstract_keyword_2.cpp  
class X abstract {  
public:  
   virtual void f() {}  
};  
  
int main() {  
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'  
                    // cannot be instantiated. See declaration of 'X'}  
  
```  
  
 **示例**  
  
 下面的代码示例生成一个错误，因为函数 `f` 包含了一个定义，但被标记为 `abstract`。  示例中的最后一条语句显示声明抽象虚拟函数等效于声明纯虚拟函数。  
  
```  
// abstract_keyword_3.cpp  
// compile with: /clr  
ref class X {  
public:  
   virtual void f() abstract {}   // C3634  
   virtual void g() = 0 {}   // C3634  
};  
```  
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)
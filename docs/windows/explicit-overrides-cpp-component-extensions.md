---
title: "显式重写 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "重写, 重写 [C++]"
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
caps.latest.revision: 21
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 显式重写
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题讨论如何显式重写基类或接口的成员。  应只使用一个名为 \(显式\) 重写用具有不同名称的派生方法的方法。  
  
## 所有运行时  
 **语法**  
  
```  
  
        overriding-function-declarator = type::function [,type::function] { overriding-function-definition }  
overriding-function-declarator = function { overriding-function-definition }  
```  
  
 **参数**  
  
 *overriding\-function\-declarator*  
 重写函数的返回类型、名称和参数列表。注意重写函数不必与重写函数相同。  
  
 *type*  
 包含一个函数覆盖的基类型。  
  
 *function*  
 重写的一个或多个函数名称一个逗号分隔列表。  
  
 *overriding\-function\-definition*  
 定义重写函数的函数体语句。  
  
 **备注**  
  
 使用显式重写方法的签名创建别名，还是为方法提供的不同实现具有相同的签名。  
  
 有关修改继承的类型和类型成员的继承行为的信息，请参见 [重写说明符](../windows/override-specifiers-cpp-component-extensions.md)。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
  
### 要求  
 编译器选项：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **备注**  
  
 有关显式重写信息用本机代码或使用 **\/clr:oldSyntax**编译，请参见 [显式重写](../cpp/explicit-overrides-cpp.md)。  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 下面的代码示例显示成员的简单，隐式重写和实现在基接口，而不是使用显式重写。  
  
```  
// explicit_override_1.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
}  
```  
  
 **Output**  
  
  **I1::f 的 X::f 重写** **示例**  
  
 使用显式重写语法，下面的代码示例演示如何实现具有的公用签名的所有接口成员中，  
  
```  
  
// explicit_override_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
interface struct I2 {  
   virtual void f();  
};  
  
ref struct X : public I1, I2 {  
   virtual void f() = I1::f, I2::f {  
      System::Console::WriteLine("X::f override of I1::f and I2::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   I2 ^ MyI2 = gcnew X;  
   MyI -> f();  
   MyI2 -> f();  
}  
```  
  
 **Output**  
  
  **X::f 重写 I1::f 和 I2::f**  
 **X::f 重写 I1::f 和 I2::f** **示例**  
  
 下面的代码示例显示如何重写函数可以有其实现从函数不同的名称。  
  
```  
// explicit_override_3.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void g() = I1::f {  
      System::Console::WriteLine("X::g");  
   }  
};  
  
int main() {  
   I1 ^ a = gcnew X;  
   a->f();  
}  
```  
  
 **Output**  
  
  **X::g** **示例**  
  
 下面的代码示例演示如何实现一个类型安全的集合显式接口实现。  
  
```  
// explicit_override_4.cpp  
// compile with: /clr /LD  
using namespace System;  
ref class R : ICloneable {  
   int X;  
  
   virtual Object^ C() sealed = ICloneable::Clone {  
      return this->Clone();  
   }  
  
public:  
   R() : X(0) {}  
   R(int x) : X(x) {}  
  
   virtual R^ Clone() {  
      R^ r = gcnew R;  
      r->X = this->X;  
      return r;  
   }  
};  
```  
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)
---
title: "sealed（C++ 组件扩展） | Microsoft Docs"
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
  - "sealed_cpp"
  - "sealed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sealed 关键字 [C++]"
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# sealed（C++ 组件扩展）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`sealed` 是 ref 类的上下文相关关键字，它指示某个虚拟成员不能被替代，或某个类型不能用作基类型。  
  
> [!NOTE]
>  ISO C\+\+11 标准语言具有 [final](../cpp/final-specifier.md) 关键字，它在 Visual Studio 中受到支持。  在标准类上使用 `final`，在 ref 类上使用 `sealed`。  
  
## 所有运行时  
 **语法**  
  
```  
  
ref class identifier sealed {...};  
virtual return-type identifier() sealed {...};  
  
```  
  
 **参数**  
  
 *标识符*  
 函数或类的名称。  
  
 *返回类型*  
 函数返回的类型。  
  
 **备注**  
  
 在第一个语法示例中，密封了类。  在第二个示例中，密封了虚函数。  
  
 `sealed` 关键字对于本机目标有效，它同时对于 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 和公共语言运行时 \(CLR\) 有效。  有关详细信息，请参阅[“替代说明符和本机编译”](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。  
  
 你可以检测到是否在编译时使用 `__is_sealed (``type``)` 类型特征密封了某个类型。  有关详细信息，请参阅[编译器使用类型特征支持](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 `sealed` 是上下文相关的关键字。  有关详细信息，请参阅[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 请参阅[“Ref 类和结构”](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx)。  
  
### 要求  
 编译器选项：**\/ZW**  
  
## 公共语言运行时  
 （此语言功能没有只适用于公共运行时的备注。）  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 下面的这个代码示例显示虚拟成员上 `sealed` 的效果。  
  
```cpp  
// sealed_keyword.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
   virtual void g();  
};  
  
ref class X : I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
  
   virtual void g() sealed {  
      System::Console::WriteLine("X::f override of I1::g");  
   }  
};  
  
ref class Y : public X {  
public:  
   virtual void f() override {  
      System::Console::WriteLine("Y::f override of I1::f");  
   }  
  
   /*  
   // the following override generates a compiler error  
   virtual void g() override {  
      System::Console::WriteLine("Y::g override of I1::g");  
   }    
   */  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
   MyI -> g();  
  
   I1 ^ MyI2 = gcnew Y;  
   MyI2 -> f();  
}  
```  
  
 **输出**  
  
  **X::f override of I1::f**  
 **X::f override of I1::g**  
 **Y::f override of I1::f** 下一个代码示例演示如何将类标记为已密封。  
  
```cpp  
// sealed_keyword_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X sealed : I1 {  
public:  
   virtual void f() override {}  
};  
  
ref class Y : public X {   // C3246 base class X is sealed  
public:  
   virtual void f() override {}  
};  
```  
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)
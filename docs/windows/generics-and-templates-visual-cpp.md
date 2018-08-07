---
title: 泛型和模板 （Visual c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3ebb476b0a8c384759c9d44101e7bac7083103b2
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570761"
---
# <a name="generics-and-templates-visual-c"></a>泛型和模板 (Visual C++)
泛型和模板是为参数化类型提供支持这两种语言功能。 但是，它们不同，并且具有不同用途。 本主题概述了很多差异。  
  
 有关详细信息，请参阅[Windows 运行时和托管模板](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md)。  
  
## <a name="comparing-templates-and-generics"></a>比较模板和泛型  
 泛型和 c + + 模板之间的主要区别：  
  
-   泛型是泛型，直到它们在运行时替换类型。 模板被专门在编译时，因此它们不是在运行时仍参数化的类型  
  
-   公共语言运行时在 MSIL 中专门支持泛型。 因为运行时知道泛型，可以将特定类型替换为泛型类型引用包含泛型类型的程序集时。 模板，与此相反，解析为普通类型在编译时并不可能在其他程序集中专用化的结果类型。  
  
-   泛型专门从事于两个不同的程序集具有相同类型参数具有相同的类型。 模板专用化中使用相同的类型参数被视为由运行时为不同类型的两个不同的程序集。  
  
-   泛型生成的单个可执行代码，用于进行的所有引用类型参数 （这不是适用于具有相同的实现，每个值类型的值类型）。 JIT 编译器知道泛型且可以优化用作类型参数的引用或值类型的代码。 模板将生成单独的运行时代码对于每个专用化。  
  
-   泛型不允许非类型模板参数，如`template <int i> C {}`。 模板允许使用它们。  
  
-   泛型不允许显式专用化 （即，自定义的特定类型的模板实现）。 模板执行操作。  
  
-   泛型不允许部分专用化 （的自定义实现为子集的类型参数）。 模板执行操作。  
  
-   不允许泛型类型参数用作泛型类型的基类。 模板执行操作。  
  
-   模板支持模板模板参数 (例如`template<template<class T> class X> class MyClass`)，但泛型不这样做。  
  
## <a name="combining-templates-and-generics"></a>结合使用模板和泛型  
  
-   泛型中的基本差异影响构建应用程序的组合模板和泛型。 例如，假设你想要创建的泛型包装器来公开作为泛型该模板与其他语言的模板类。 不能具有泛型 take 然后传递到模板，因为该模板需要具有在编译时，该类型形参的类型参数，但一般不会直到运行时解析类型参数。 嵌套在泛型模板不可行，是因为没有方法在编译时无法在运行时实例化的任意泛型类型的扩展模板。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例演示使用模板和泛型在一起的一个简单示例。 在此示例中，模板类将通过其参数传递给泛型类型。 不能反过来。  
  
 当你想要对现有泛型 API，是对 Visual c + + 程序集，本地的模板代码生成时或当您需要将一层额外的参数化添加到泛型类型，若要利用的模板不 supporte 某些功能时，可以使用此习惯用法通过泛型 d。  
  
### <a name="code"></a>代码  
  
```cpp  
// templates_and_generics.cpp  
// compile with: /clr  
using namespace System;  
  
generic <class ItemType>  
ref class MyGeneric {  
   ItemType m_item;  
  
public:  
   MyGeneric(ItemType item) : m_item(item) {}  
   void F() {   
      Console::WriteLine("F");   
   }  
};  
  
template <class T>  
public ref class MyRef {  
MyGeneric<T>^ ig;  
  
public:  
   MyRef(T t) {  
      ig = gcnew MyGeneric<T>(t);  
      ig->F();  
    }      
};  
  
int main() {  
   // instantiate the template  
   MyRef<int>^ mref = gcnew MyRef<int>(11);  
}  
```  
  
### <a name="output"></a>输出  
  
```Output  
F  
```  
  
## <a name="see-also"></a>请参阅  
 [泛型](../windows/generics-cpp-component-extensions.md)
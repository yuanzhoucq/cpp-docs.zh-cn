---
title: "泛型和模板 （Visual c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 307cc39e64a6fd91f3f5f96da634e47d3e9a9030
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="generics-and-templates-visual-c"></a>泛型和模板 (Visual C++)
泛型和模板是参数化类型为提供支持这两种语言功能。 但是，它们不同，并且具有不同的用途。 本主题概述了许多差异。  
  
 有关详细信息，请参阅[Windows 运行时和托管模板](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md)。  
  
## <a name="comparing-templates-and-generics"></a>比较模板和泛型  
 泛型和 c + + 模板之间的主要差异：  
  
-   泛型是泛型，直到类型在运行时将替换为它们的。 模板是在编译时专用，因此不会在运行时仍参数化的类型  
  
-   公共语言运行时在 MSIL 中专门支持泛型。 因为运行时知道有关泛型，则引用包含泛型类型的程序集时，泛型类型可以替换特定的类型。 模板，与此相反，解析为普通类型在编译时并不可能在其他程序集专用化在产生的类型。  
  
-   泛型专业的两个不同的程序集具有相同的类型自变量具有相同的类型。 模板专用化中使用相同的类型自变量被视为由运行时为不同类型的两个不同的程序集。  
  
-   泛型将生成为一段单独的可执行代码时使用 （不能同时运行对于值类型，具有每个值类型的唯一实现） 的所有引用类型参数。 JIT 编译器识别泛型的并且能够优化用作类型参数的引用或值类型的代码。 模板生成每个专用化的单独的运行时代码。  
  
-   泛型不允许非类型模板参数，如`template <int i> C {}`。 模板允许它们。  
  
-   泛型不允许显式专用化 （即，为特定类型的模板的自定义实现）。 模板执行操作。  
  
-   泛型不允许部分专用化 （的自定义实现子集的类型自变量）。 模板执行操作。  
  
-   泛型不允许类型参数用作泛型类型的基类。 模板执行操作。  
  
-   模板支持模板模板参数 (例如`template<template<class T> class X> class MyClass`)，但不为泛型。  
  
## <a name="combining-templates-and-generics"></a>组合模板和泛型  
  
-   泛型中的基本差异有用于生成结合模板和泛型的应用程序的影响。 例如，假设有一种模板类，你想要创建泛型包装器来公开到其他语言将该模板为泛型。 不能具有泛型 take 然后传递到该模板后，因为模板需要先在编译时，具有该类型参数的类型参数，但泛型不会在运行时解析类型参数。 嵌套泛型中的模板将不起作用是因为没有方法在任意无法在运行时实例化的泛型类型的编译时扩展模板。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例演示使用模板和泛型在一起的一个简单的示例。 在此示例中，此模板类将通过其参数传递给泛型类型。 反之不可能。  
  
 当你想要在现有泛型 API，是对 Visual c + + 程序集，本地的模板代码生成，或当你需要将一层额外的参数化添加到泛型类型，以利用模板不 supporte 的某些功能时，无法使用此习惯用法通过泛型 d。  
  
### <a name="code"></a>代码  
  
```  
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
  
```  
F  
```  
  
## <a name="see-also"></a>请参阅  
 [泛型](../windows/generics-cpp-component-extensions.md)
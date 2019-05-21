---
title: 泛型与模板 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
ms.openlocfilehash: 74cfd791e8400b788d38f272eed3d421ca4230e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516352"
---
# <a name="generics-and-templates-ccli"></a>泛型与模板 (C++/CLI)

泛型和模板都是支持参数化类型的语言功能。 但它们是不同的，而且用途也不同。 本主题概述了它们的许多区别。

有关详细信息，请参阅 [Windows 运行时和托管模板](windows-runtime-and-managed-templates-cpp-component-extensions.md)。

## <a name="comparing-templates-and-generics"></a>比较模板与泛型

泛型与 C++ 模板的主要区别：

- 泛型在运行时被类型替换前一直都是泛型。 模板在编译时专用化，所以在运行时仍不是参数化类型

- 公共语言运行时在 MSIL 中专门支持泛型。 因为运行时知道泛型，所以在引用包含泛型类型的程序集时，可以用特定类型替换泛型类型。 相比之下，模板在编译时解析为普通类型，所以生成的类型可能不会在其他程序集中专用化。

- 在两个包含相同类型参数的不同程序集中专用化的泛型为相同类型。 运行时将在两个包含相同类型参数的不同程序集中专用化的模板视为不同类型。

- 泛型作为一段可执行代码生成，用于所有引用类型参数（这不适用于值类型，每个值类型都有一个唯一实现）。 JIT 编译器知道泛型，并能为用作类型参数的引用类型或值类型优化代码。 模板为每个专用化单独生成运行时代码。

- 泛型禁止使用非类型模板参数（如 `template <int i> C {}`）。 但模板允许使用。

- 泛型禁止使用显式专用化（即特定类型的模板的自定义实现）。 但模板允许使用。

- 泛型禁止使用部分专用化（即部分类型参数的自定义实现）。 但模板允许使用。

- 泛型禁止将类型参数用作泛型类型的基类。 但模板允许使用。

- 模板支持模板-模板参数（例如 `template<template<class T> class X> class MyClass`），但泛型不支持。

## <a name="combining-templates-and-generics"></a>结合使用模板和泛型

泛型与模板的基本区别对生成结合使用模板和泛型的应用程序有一定影响。 例如，假设有一个模板类，你希望通过创建泛型包装器来将此模板作为泛型公开给其他语言。 无法让泛型获取它随后将传递给模板的类型参数，因为模板需要在编译时获取此类型参数，而泛型要到运行时才会解析类型参数。 将模板嵌套在泛型中也不起作用，因为无法在编译时为任意可以在运行时实例化的泛型类型扩展模板。

## <a name="example"></a>示例

### <a name="description"></a>说明

下面的简单示例展示了如何结合使用模板和泛型。 在此示例中，模板类将它的参数传递给泛型类型。 反之则不行。

若要使用 C++/CLI 程序集的本地模板代码在现有泛型 API 的基础上进行生成，或者需要向泛型类型添加额外的参数化层，以利用泛型不支持的特定模板功能，也是反之则不行。

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

```Output
F
```

## <a name="see-also"></a>请参阅

[泛型](generics-cpp-component-extensions.md)
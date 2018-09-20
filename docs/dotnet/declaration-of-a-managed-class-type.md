---
title: 托管的类类型的声明 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __gc types
- classes [C++], managed
- class keyword [C++], CLR
- __value keyword
- value types, declaring
- value keyword [C++]
- managed classes
- interface class keyword
- ref keyword [C++]
ms.assetid: 16de9c94-91d7-492f-8ac7-f0729cc627e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0f9ceb0867fbdfbbdb46075662fca802d1ee0bba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393667"
---
# <a name="declaration-of-a-managed-class-type"></a>托管类类型的声明

声明引用类类型，Visual c + + 中与 c + + 托管扩展的方法。

在托管扩展中，引用类类型开头`__gc`关键字。 在新语法中，`__gc`关键字替换为两个空格分隔的关键字之一：`ref class`或`ref struct`。 所选的`struct`或`class`指示公共 (对于`struct`) 或专用 (对于`class`) 初始未标记的类型的正文节中声明其成员的默认访问级别。

同样，在托管扩展中，值类类型开头，但`__value`关键字。 在新语法中，`__value`关键字替换为两个空格分隔的关键字之一：`value class`或`value struct`。

使用关键字指示了一个接口类型，在托管扩展`__interface`。 在新语法中，这将替换`interface class`。

例如，下面的类声明中的托管扩展：

```
public __gc class Block {};     // reference class
public __value class Vector {}; // value class
public __interface IFooBar {};  // interface class
```

在新语法中的等效声明，如下所示：

```
public ref class Block {};         // reference class
public value class Vector {};      // value class
public interface class IFooBar {}; // interface class
```

## <a name="specifying-the-class-as-abstract"></a>指定的类为抽象

在托管扩展中，将关键字`__abstract`之前`class`关键字 (之前或之后`__gc`) 以指示的类是不完整，且不能在程序内创建的类的对象：

```
public __gc __abstract class Shape {};
public __gc __abstract class Shape2D: public Shape {};
```

在新语法中，您指定`abstract`上下文关键字之后类名，并且之前类的主体、 基类派生列表或分号。

```
public ref class Shape abstract {};
public ref class Shape2D abstract : public Shape{};
```

当然，语义含义保持不变。

## <a name="specifying-the-class-as-sealed"></a>指定类为密封类

在托管扩展中，将关键字`__sealed`之前`class`关键字 (之前或之后`__gc`) 以指示类的对象不能被继承：

```
public __gc __sealed class String {};
```

在新语法中，您指定`sealed`上下文关键字之后类名，并且之前类的主体、 基类派生列表或分号。

可以同时派生一个类和密封它。 例如，`String`类隐式派生自`Object`。 密封类的好处是它支持静态解析 (即，在编译时) 的所有虚拟函数调用通过密封的引用类对象。 这是因为`sealed`说明符保证`String`跟踪句柄无法随后派生的类可能会提供重写虚拟方法调用的实例的引用。 下面是一个密封类的示例中新的语法：

```
public ref class String sealed {};
```

一个还可以指定一个类为这两个抽象和密封-这是一个指示静态类的特殊情况。 这是文档中所述 CLR，如下所示：

"一个类型，同时`abstract`和`sealed`应仅静态成员，可作为什么某些语言中调用一个命名空间。"

例如，下面是一个抽象密封类，使用托管扩展语法的声明：

```
public __gc __sealed __abstract class State {
public:
   static State() {}
   static bool inParamList();

private:
   static bool ms_inParam;
};
```

而以下是此声明转换为新的语法：

```
public ref class State abstract sealed {
public:
   static State();
   static bool inParamList();

private:
   static bool ms_inParam;
};
```

## <a name="clr-inheritance-specifying-the-base-class"></a>CLR 继承： 指定的基类

在 CLR 对象模式下支持仅公共单一继承。 但是，托管扩展保留基类没有与指定私有派生访问关键字的 ISO c + + 默认解释。 这意味着每个 CLR 继承声明必须以提供`public`关键字重写默认值解释。

```
// Managed Extensions: error: defaults to private derivation
__gc class Derived : Base {};
```

在新的语法定义中，缺少访问关键字指示 CLR 继承定义中的公共派生。 因此，`public`访问关键字现在为可选项。 虽然这不需要任何修改托管扩展 c + + 代码，我列出了出于完整性的考虑此更改。

```
// New syntax: ok: defaults to public derivation
ref class Derived : Base{};
```

## <a name="see-also"></a>请参阅

[将托管类型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[abstract](../windows/abstract-cpp-component-extensions.md)<br/>
[sealed](../windows/sealed-cpp-component-extensions.md)
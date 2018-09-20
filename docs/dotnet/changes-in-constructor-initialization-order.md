---
title: 构造函数初始化顺序中的更改 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors, C++
ms.assetid: 8892c38d-6bf7-4cf7-ac8f-15e052135a79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fd54e9810131f3ddfabe458c70ddef081568a9cd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397684"
---
# <a name="changes-in-constructor-initialization-order"></a>以构造函数初始化顺序进行更改

类构造函数的初始化顺序已从托管扩展中的 c + + 更改为 Visual c + +。

## <a name="comparison-of-constructor-initialization-order"></a>构造函数初始化顺序的比较

在 c + + 托管扩展中，构造函数初始化按以下顺序出现：

1. 调用的构造函数的基类，如果有的话，是。

1. 计算此类的初始化列表。

1. 执行类构造函数的代码体。

执行此顺序将遵循相同的约定，如本机 c + + 编程中所示。 新的 Visual c + + 语言规定了 CLR 类的以下执行顺序：

1. 计算此类的初始化列表。

1. 调用的构造函数的基类，如果有的话，是。

1. 执行类构造函数的代码体。

请注意此更改仅适用于 CLR 类;Visual c + + 中的本机类仍遵循以前的约定。 在这两种情况下，这些规则将向上层叠在整个给定类的整个层次结构链。

请考虑下面的代码示例使用 c + + 托管扩展：

```
__gc class A
{
public:
   A() : _n(1)
   {
   }

protected:
   int _n;
};

__gc class B : public A
{
public:
   B() : _m(_n)
   {
   }
private:
   int _m;
};
```

按照上述构造函数初始化顺序，我们应看到以下顺序执行新的类的实例`B`构造：

1. 基类的构造函数`A`调用。 `_n`成员被初始化为`1`。

1. 类的初始化列表`B`进行计算。 `_m`成员被初始化为`1`。

1. 类的代码正文`B`执行。

现在请考虑在新的 Visual c + + 语法相同的代码：

```
ref class A
{
public:
   A() : _n(1)
   {
   }

protected:
   int _n;
};

ref class B : A
{
public:
   B() : _m(_n)
   {
   }
private:
   int _m;
};
```

当新的执行顺序类的实例`B`构造在新语法是：

1. 类的初始化列表`B`进行计算。 `_m`成员被初始化为`0`(`0`是未初始化的值`_m`类成员)。

1. 基类的构造函数`A`调用。 `_n`成员被初始化为`1`。

1. 类的代码正文`B`执行。

请注意类似的语法生成不同的结果，这些代码示例。 类的构造函数`B`取决于从基类值`A`来初始化其成员。 但是，类的构造函数`A`尚未调用。 当继承的类取决于基类构造函数中发生的内存或资源分配时，此类依赖项将是非常危险。

## <a name="what-this-means-going-from-managed-extensions-for-c-to-visual-c-2010"></a>从托管扩展 c + + 转到 Visual c + + 2010年此含义

在许多情况下对类构造函数的执行顺序的更改应透明的程序员，因为基类继承的类的行为没有概念。 但是，如以下代码示例所示，继承的类的构造函数时可能会极大地影响其初始化列表依赖于基类成员的值。 中的代码移动托管扩展 c + + 的新语法，请考虑移动到类构造函数中，为保证执行大量此类构造上次发生。

## <a name="see-also"></a>请参阅

[将托管类型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[构造函数](../cpp/constructors-cpp.md)

---
title: 编译器错误 C2558
ms.date: 11/04/2016
f1_keywords:
- C2558
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
ms.openlocfilehash: 2504b42f49ccb040f676f0aead8f243d33c7dd1a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207740"
---
# <a name="compiler-error-c2558"></a>编译器错误 C2558

“identifier”: 没有可用的复制构造函数或复制构造函数声明为“explicit”

复制构造函数从同一类型的另一个对象初始化某对象。 （它创建对象的副本。）如果未定义任何构造函数，编译器将生成一个默认的复制构造函数。

### <a name="to-fix-this-error"></a>修复此错误的方法

1. 尝试复制其复制构造函数为的类时，可能出现此问题 **`private`** 。 在大多数情况下， **`private`** 不应复制具有复制构造函数的类。 常见编程技术声明 **`private`** 复制构造函数以防止直接使用类。 该类本身可能无用，或需要另一个类才能正常工作。

   如果你确定可以安全地使用具有 **`private`** 复制构造函数的类，请从具有构造函数的类派生新类， **`private`** 并使 **`public`** 或 **`protected`** 复制构造函数在新类中可用。 使用该派生类替代原始类。

1. 在尝试复制其复制构造函数为显式的类时，可能出现该问题。 将复制构造函数声明为 **`explicit`** 会阻止将类的对象传递到函数或从函数返回类的对象。 有关显式构造函数的详细信息，请参阅[用户定义的类型转换](../../cpp/user-defined-type-conversions-cpp.md)。

1. 如果尝试复制 **`const`** 通过使用不带引用参数的复制构造函数声明的类实例，则会出现此问题 **`const`** 。 使用 **`const`** 类型引用而不是非常量类型引用声明复制构造函数。

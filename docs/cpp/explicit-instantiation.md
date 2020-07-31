---
title: 显式实例化
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: 4b1808791110c4eed237d18436897dac59170206
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232295"
---
# <a name="explicit-instantiation"></a>显式实例化

您可以使用显式实例化来创建模板化类或函数的实例化，而不用将其实际用于您的代码。 由于在创建使用模板进行分发的库（.lib）文件时，此方法非常有用，未实例化的模板定义不会放入对象（.obj）文件中。

此代码 `MyStack` 为 **`int`** 变量和六项显式实例化：

```cpp
template class MyStack<int, 6>;
```

该语句创建 `MyStack` 的实例化，而不保留对象的任何存储。 为所有成员生成代码。

下一行仅显式实例化构造函数成员函数：

```cpp
template MyStack<int, 6>::MyStack( void );
```

您可以通过使用特定类型参数重新声明函数模板来显式实例化它们，如[函数模板实例化](../cpp/function-template-instantiation.md)中的示例中所示。

可以使用 **`extern`** 关键字来阻止成员的自动实例化。 例如：

```cpp
extern template class MyStack<int, 6>;
```

同样，您可以将特定成员标记为外部且未实例化：

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

可以使用 **`extern`** 关键字来防止编译器在多个对象模块中生成相同的实例化代码。 如果调用该函数，则必须在至少一个链接的模块中使用指定的显式模板参数来实例化模板函数，否则会在生成程序时收到链接器错误。

> [!NOTE]
> **`extern`** 专用化中的关键字仅适用于在类体的外部定义的成员函数。 在类声明中定义的函数被视为内联函数并始终实例化。

## <a name="see-also"></a>另请参阅

[函数模板](../cpp/function-templates.md)

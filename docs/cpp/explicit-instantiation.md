---
title: 显式实例化
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: 0b1290bc23c56c0f35ddd3bb93e37ce4f5f0d2ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361959"
---
# <a name="explicit-instantiation"></a>显式实例化

您可以使用显式实例化来创建模板化类或函数的实例化，而不用将其实际用于您的代码。 由于在创建使用模板进行分发的库 （.lib） 文件时，这非常有用，因此未实例化的模板定义不会放入对象 （.obj） 文件中。

此代码显式实例化`MyStack`**int**变量和六个项目：

```cpp
template class MyStack<int, 6>;
```

该语句创建 `MyStack` 的实例化，而不保留对象的任何存储。 为所有成员生成代码。

下一行仅显式实例化构造函数成员函数：

```cpp
template MyStack<int, 6>::MyStack( void );
```

可以使用特定类型参数显式实例化函数模板以重新声明它们，如[函数模板实例化](../cpp/function-template-instantiation.md)中的示例所示。

您可以使用**extern**关键字来防止成员的自动实例化。 例如：

```cpp
extern template class MyStack<int, 6>;
```

同样，您可以将特定成员标记为外部且未实例化：

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

可以使用**extern**关键字来防止编译器在多个对象模块中生成相同的实例化代码。 如果调用该函数，则必须在至少一个链接的模块中使用指定的显式模板参数来实例化模板函数，否则会在生成程序时收到链接器错误。

> [!NOTE]
> 专业化化中的**extern**关键字仅适用于在类正文之外定义的成员函数。 在类声明中定义的函数被视为内联函数，并且始终被实例化。

## <a name="see-also"></a>另请参阅

[函数模板](../cpp/function-templates.md)

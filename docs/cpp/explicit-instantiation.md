---
title: 显式实例化 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85ea920dc01f408c7723fb082e6a0e60fa9a00e8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110661"
---
# <a name="explicit-instantiation"></a>显式实例化

你可以使用显式实例化来创建模板化类或函数的实例化，而不用将其实际用于你的代码。 创建库 (.lib) 文件，使用模板进行分发时，这很有用，因为未实例化的模板定义不会被放到对象 (.obj) 文件。

此代码显式实例化`MyStack`有关**int**变量和六个项：

```cpp
template class MyStack<int, 6>;
```

该语句创建 `MyStack` 的实例化，而不保留对象的任何存储。 为所有成员生成代码。

下一行仅显式实例化构造函数成员函数：

```cpp
template MyStack<int, 6>::MyStack( void );
```

您可以显式实例化函数模板使用特定类型参数重新声明它们中的示例中所示[函数模板实例化](../cpp/function-template-instantiation.md)。

可以使用**extern**关键字以防止自动实例化的成员。 例如：

```cpp
extern template class MyStack<int, 6>;
```

同样，您可以将特定成员标记为外部且未实例化：

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

可以使用**extern**关键字阻止编译器在多个对象模块中生成相同的实例化代码。 如果调用该函数，则必须在至少一个链接的模块中使用指定的显式模板参数来实例化模板函数，否则会在生成程序时收到链接器错误。

> [!NOTE]
>  **Extern**专用化中的关键字仅适用于在类主体外部定义成员函数。 类声明中定义的函数被视为内联函数，并始终实例化。

## <a name="see-also"></a>请参阅

[函数模板](../cpp/function-templates.md)
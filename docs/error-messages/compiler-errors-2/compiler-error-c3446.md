---
title: 编译器错误 C3446
ms.date: 07/21/2017
f1_keywords:
- C3446
helpviewer_keywords:
- C3445
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
ms.openlocfilehash: 8145e0cdd97022ebdcc1a7ce38c8860a005945b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631111"
---
# <a name="compiler-error-c3446"></a>编译器错误 C3446

>'*类*： 不允许的值类成员使用的默认成员初始值设定项

在 Visual Studio 2015 及更早版本中，编译器允许（但会忽略）值类成员的默认成员初始值设定项。 值类的默认初始化始终对成员执行零初始化；不允许使用默认构造函数。 在 Visual Studio 2017 中，默认成员初始值设定项引发编译器错误，如下例所示：

## <a name="example"></a>示例

下面的示例生成 C3446 Visual Studio 2017 及更高版本：

```cpp
// C3446.cpp
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer
                  // is not allowed for a member of a value class
       int j {0}; // C3446
};
```

若要更正此错误，删除初始值设定项：

```cpp
// C3446b.cpp
value struct V
{
       int i;
       int j;
};
```


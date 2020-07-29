---
title: 编译器错误 C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: 1555817de6e50ea27a021718c8b094efeaebacde
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230839"
---
# <a name="compiler-error-c3551"></a>编译器错误 C3551

“应为后期指定的返回类型”

如果使用 **`auto`** 关键字作为函数返回类型的占位符，则必须提供一个后期指定的返回类型。 在下面的示例中，函数的后期指定返回类型 `myFunction` 是一个指针，指向类型的四个元素的数组 **`int`** 。

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>另请参阅

[auto](../../cpp/auto-cpp.md)

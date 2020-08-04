---
title: 联合的存储
ms.date: 11/04/2016
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
ms.openlocfilehash: 64e8b5184eeccd4de6d196e40ec464807bec93e7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211653"
---
# <a name="storage-of-unions"></a>联合的存储

与联合变量关联的存储是联合的最大成员所需的存储。 在存储较小的成员时，联合变量可以包含未使用的内存空间。 所有成员都存储在同一内存空间中并以相同的地址开始。 每次将值赋给不同的成员时，都会重写存储的值。 例如：

```
union         /* Defines a union named x */
{
    char *a, b;
    float f[20];
} x;
```

按照声明的顺序，`x` 联合的成员是指向 `char` 值的指针、`char` 值和包含 `float` 值的数组。 由于 `x` 是联合的最长成员，因此为 `f` 分配的存储是 20 个元素数组 `f` 所需的存储。 由于没有与联合关联的标记，因此其类型是未命名的或“匿名的”。

## <a name="see-also"></a>请参阅

[联合声明](../c-language/union-declarations.md)

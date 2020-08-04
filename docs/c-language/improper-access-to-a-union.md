---
title: 对联合的不正确的访问
ms.date: 11/04/2016
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
ms.openlocfilehash: 5a804ed80c8f1ac2f5dd9a24f12c67e96e199b6b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227824"
---
# <a name="improper-access-to-a-union"></a>对联合的不正确的访问

**ANSI 3.3.2.3** 使用不同类型的成员访问联合对象的成员

如果声明两个类型的联合并存储一个值，但使用其它类型访问该联合，则结果是不可靠的。

例如，声明了 `float` 和 `int` 的联合。 存储 `float` 值，但程序稍后会将此值作为 `int` 进行访问。 在这种情况下，此值取决于 `float` 值的内部存储。 整数值是不可靠的。

## <a name="see-also"></a>请参阅

[结构、联合、枚举和位域](../c-language/structures-unions-enumerations-and-bit-fields.md)

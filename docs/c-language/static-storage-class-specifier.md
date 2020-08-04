---
title: 静态存储类说明符
ms.date: 11/04/2016
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
ms.openlocfilehash: e84e2745c6077f038f47295119936a1ad6431bdd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229488"
---
# <a name="static-storage-class-specifier"></a>静态存储类说明符

在内部级别使用 `static` 存储类说明符声明的变量有全局生存期，但它仅在声明它的块中可见。 对于常数字符串，使用 `static` 是有用的，因为它减轻了频繁初始化经常调用的函数的开销。

## <a name="remarks"></a>备注

如果没有显式初始化 `static` 变量，则它默认初始化为 0。 在函数内，`static` 会导致存储被分配并用作定义。 内部静态变量仅提供对单个函数可见的私有永久存储。

## <a name="see-also"></a>请参阅

[C 存储类](c-storage-classes.md)<br/>
[存储类 (C++)](../cpp/storage-classes-cpp.md)

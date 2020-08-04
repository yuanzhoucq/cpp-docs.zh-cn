---
title: 指针减法
ms.date: 11/04/2016
helpviewer_keywords:
- pointer subtraction
ms.assetid: 4d515690-088a-43f6-bb8c-57b849f7ccf7
ms.openlocfilehash: ab141f9c862c7d3a8f7e939c021c0fd1ed9487fe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211744"
---
# <a name="pointer-subtraction"></a>指针减法

**ANSI 3.3.6, 4.1.1** 保留两个指向同一数组 ptrdiff_t  的元素的指针之间的差所需的整数类型

在 32 位 x86 平台上，`ptrdiff_t` typedef 是 `int`。 在 64 位平台上，`ptrdiff_t` typedef 是 `__int64`。

## <a name="see-also"></a>请参阅

[数组和指针](../c-language/arrays-and-pointers.md)

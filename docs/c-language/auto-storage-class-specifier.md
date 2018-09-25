---
title: auto 存储类说明符 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca42eb26cc6bb08cd8a05e31b23e004b1cbeb8b2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057426"
---
# <a name="auto-storage-class-specifier"></a>auto 存储类说明符

auto 存储类说明符可声明自动变量，即具有本地生存期的变量。 auto 变量仅在声明它的块中可见。 auto 变量的声明可包含初始值设定项，如[初始化](../c-language/initialization.md)中所述。 由于具有 auto 存储类的变量不会自动初始化，因此应该在声明这些变量时对其进行显式初始化，或在块的语句中为其分配初始值。 未初始化的 auto 变量的值是不确定的。 （如果给定了初始值设定项，则每次 auto 或 register 存储类的局部变量进入此范围时都会被初始化。）

内部 static 变量（具有本地或块范围的静态变量）可以使用任何外部或 static 项的地址进行初始化，但不能使用另一个 auto 项的地址进行初始化，因为 auto 项的地址不是常量。

## <a name="see-also"></a>请参阅

[auto 关键字](../cpp/auto-keyword.md)
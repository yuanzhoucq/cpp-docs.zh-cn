---
title: 编译器错误 C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: e9a4ce2276a602d59e495a2f336bb9d59dc0cc99
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200754"
---
# <a name="compiler-error-c3551"></a>编译器错误 C3551

“应为后期指定的返回类型”

如果你使用 `auto` 关键字作为函数返回类型的占位符，必须提供后指定返回类型。 在下面的示例中，函数 `myFunction` 的后期指定返回类型是一个指针，该指针指向由四个 `int`类型的元素组成的数组。

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>另请参阅

[auto](../../cpp/auto-cpp.md)

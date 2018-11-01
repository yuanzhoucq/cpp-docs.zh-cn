---
title: 编译器错误 C2081
ms.date: 11/04/2016
f1_keywords:
- C2081
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
ms.openlocfilehash: 2bccd15b8c2b6d1c5cd6c4b536bbdaf350eb0181
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512896"
---
# <a name="compiler-error-c2081"></a>编译器错误 C2081

identifier： 非法的形参列表中的名称

标识符导致语法错误。

可以通过使用旧样式的形参列表导致此错误。 形参列表中，必须指定的正式参数的类型。

下面的示例生成 C2081:

```
// C2081.c
void func( int i, j ) {}  // C2081, no type specified for j
```

可能的解决方法：

```
// C2081b.c
// compile with: /c
void func( int i, int j ) {}
```
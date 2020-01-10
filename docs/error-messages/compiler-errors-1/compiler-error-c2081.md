---
title: 编译器错误 C2081
ms.date: 11/04/2016
f1_keywords:
- C2081
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
ms.openlocfilehash: 2e8e813d8162b9a191b6760366b52783e7c8609f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301985"
---
# <a name="compiler-error-c2081"></a>编译器错误 C2081

"identifier"：形参表中的名称非法

标识符导致语法错误。

此错误的原因可能是使用了形参表的旧样式。 必须在形参表中指定形参的类型。

下面的示例生成 C2081：

```c
// C2081.c
void func( int i, j ) {}  // C2081, no type specified for j
```

可能的解决方法：

```c
// C2081b.c
// compile with: /c
void func( int i, int j ) {}
```

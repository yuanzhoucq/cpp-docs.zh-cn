---
title: 编译器错误 C2092
ms.date: 11/04/2016
f1_keywords:
- C2092
helpviewer_keywords:
- C2092
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
ms.openlocfilehash: d3d0b0e62fbc5f8ad90b3fee5fe39c6bdaba7c2e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375999"
---
# <a name="compiler-error-c2092"></a>编译器错误 C2092

数组 name 数组元素类型不能是函数

不允许的函数的数组。 使用指向函数的指针的数组。

## <a name="example"></a>示例

下面的示例生成 C2092:

```
// C2092.cpp
typedef void (F) ();
typedef F AT[10];   // C2092
```

## <a name="example"></a>示例

可能的解决方法：

```
// C2092b.cpp
// compile with: /c
typedef void (F) ();
typedef F * AT[10];
```
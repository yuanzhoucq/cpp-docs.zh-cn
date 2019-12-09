---
title: 编译器错误 C3452
ms.date: 11/04/2016
f1_keywords:
- C3452
helpviewer_keywords:
- C3452
ms.assetid: e5293dcf-cb70-4133-ae2a-0bb496950ba0
ms.openlocfilehash: c491217f01d8e78375401b54faa48d9db410ccad
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756716"
---
# <a name="compiler-error-c3452"></a>编译器错误 C3452

列出不是常量的参数成员

参数被传递到一个特性，但此特性需要一个常量，即一个在编译时可计算出结果的值。

## <a name="example"></a>示例

下面的示例生成 C3452。

```cpp
// C3452.cpp
// compile with: /c
int i;
[module( name="mod", type=dll, custom={i} ) ];   // C3452
// try the following line instead
// [module( name="mod", type=dll, custom={"a"} ) ];
```

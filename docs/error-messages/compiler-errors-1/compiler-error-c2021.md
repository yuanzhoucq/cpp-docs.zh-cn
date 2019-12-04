---
title: 编译器错误 C2021
ms.date: 11/04/2016
f1_keywords:
- C2021
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
ms.openlocfilehash: 24463abcf123fda285356c86e3394d7274f2f6c8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751035"
---
# <a name="compiler-error-c2021"></a>编译器错误 C2021

应输入指数值而非“character”

用作浮点常数的指数的字符不是有效的数字。 请确保使用范围中的指数。

## <a name="example"></a>示例

下面的示例生成 C2021：

```cpp
// C2021.cpp
float test1=1.175494351E;   // C2021
```

## <a name="example"></a>示例

可能的解决方法：

```cpp
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```

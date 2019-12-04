---
title: 编译器错误 C3645
ms.date: 11/04/2016
f1_keywords:
- C3645
helpviewer_keywords:
- C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
ms.openlocfilehash: 504b13aeb37fae0c350ef88798fefaec6f26c8e8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757821"
---
# <a name="compiler-error-c3645"></a>编译器错误 C3645

"function"：不能对编译为本机代码的函数使用 __clrcall

函数中存在一些关键字将导致将函数编译为本机函数。

## <a name="example"></a>示例

下面的示例生成 C3645。

```cpp
// C3645.cpp
// compile with: /clr /c
#pragma unmanaged
int __clrcall dog() {}   // C3645
```

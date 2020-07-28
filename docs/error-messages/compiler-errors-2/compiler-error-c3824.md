---
title: 编译器错误 C3824
ms.date: 11/04/2016
f1_keywords:
- C3824
helpviewer_keywords:
- C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
ms.openlocfilehash: 78081de44a834b16d34d1f88a5dc996efb1f784c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220140"
---
# <a name="compiler-error-c3824"></a>编译器错误 C3824

"member"：此类型不能出现在此上下文中（函数参数、返回类型或静态成员）

固定指针不能是函数参数、返回类型或已声明 **`static`** 。

## <a name="example"></a>示例

下面的示例生成 C3824：

```cpp
// C3824a.cpp
// compile with: /clr /c
void func() {
   static pin_ptr<int> a; // C3824
   pin_ptr<int> b; // OK
}
```

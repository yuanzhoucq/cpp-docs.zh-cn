---
title: 编译器错误 C2959
ms.date: 11/04/2016
f1_keywords:
- C2959
helpviewer_keywords:
- C2959
ms.assetid: d66bb2a8-70c3-4209-a358-b0c47f111a50
ms.openlocfilehash: a0e20ed3601babb2f4f53bc293d1dc462f9a30a7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747626"
---
# <a name="compiler-error-c2959"></a>编译器错误 C2959

泛型类或函数不能是模板的成员

有关详细信息，请参阅[Windows 运行时和托管模板](../../extensions/windows-runtime-and-managed-templates-cpp-component-extensions.md)和[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C2959。

```cpp
// C2959.cpp
// compile with: /clr /c
template <class T> ref struct S {
   generic <class U> ref struct GR1;   // C2959
};
```

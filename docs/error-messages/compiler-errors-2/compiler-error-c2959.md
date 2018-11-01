---
title: 编译器错误 C2959
ms.date: 11/04/2016
f1_keywords:
- C2959
helpviewer_keywords:
- C2959
ms.assetid: d66bb2a8-70c3-4209-a358-b0c47f111a50
ms.openlocfilehash: c45466fdf8d0c4bec67779943a5868299f05cf79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535728"
---
# <a name="compiler-error-c2959"></a>编译器错误 C2959

泛型类或函数可能不是模板的成员

有关详细信息，请参阅[Windows 运行时和托管模板](../../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md)并[泛型](../../windows/generics-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C2959。

```
// C2959.cpp
// compile with: /clr /c
template <class T> ref struct S {
   generic <class U> ref struct GR1;   // C2959
};
```
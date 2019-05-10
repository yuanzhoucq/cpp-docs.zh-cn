---
title: 编译器错误 C3085
ms.date: 11/04/2016
f1_keywords:
- C3085
helpviewer_keywords:
- C3085
ms.assetid: 1ac40bf2-f63e-439e-8921-47e6dadc8354
ms.openlocfilehash: 01ebfa0007b9acc08742c57cc0528216eabb0441
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243266"
---
# <a name="compiler-error-c3085"></a>编译器错误 C3085

“constructor”：构造函数不能是“keyword”

未正确声明构造函数。 有关更多信息，请参见 [Override Specifiers](../../extensions/override-specifiers-cpp-component-extensions.md) 。

## <a name="example"></a>示例

以下示例生成 C3085。

```
// C3085.cpp
// compile with: /c /clr
ref struct S {
   S() abstract;   // C3085
   S(S%) abstract;   // C3085
};

ref struct T {
   T() sealed {}   // C3085
   T(T%) sealed {}   // C3085
};
```
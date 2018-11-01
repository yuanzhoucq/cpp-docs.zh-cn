---
title: 编译器错误 C2674
ms.date: 11/04/2016
f1_keywords:
- C2674
helpviewer_keywords:
- C2674
ms.assetid: 7cbd70d8-d992-44d7-a5cb-dd8cf9c759d2
ms.openlocfilehash: eb56651967f8fdc33b7c76b29883b25295d752d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456805"
---
# <a name="compiler-error-c2674"></a>编译器错误 C2674

在此上下文中不允许出现泛型声明

未正确声明泛型。 有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C2674。

```
// C2674.cpp
// compile with: /clr /c
void F(generic <class T> ref class R1);   // C2674
generic <class T> ref class R2 {};   // OK
```
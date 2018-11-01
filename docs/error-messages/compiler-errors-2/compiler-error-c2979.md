---
title: 编译器错误 C2979
ms.date: 11/04/2016
f1_keywords:
- C2979
helpviewer_keywords:
- C2979
ms.assetid: 98bd9043-ec44-451e-a482-3a8e35fc7464
ms.openlocfilehash: 5d9b8e025d96e448ec9494834eb1766cafd8b677
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531015"
---
# <a name="compiler-error-c2979"></a>编译器错误 C2979

泛型中不支持显式专用化

未正确声明泛型类。  请参阅[泛型](../../windows/generics-cpp-component-extensions.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C2979。

```
// C2979.cpp
// compile with: /clr /c
generic <>
ref class Utils {};   // C2979 error

generic <class T>
ref class Utils2 {};   // OK
```
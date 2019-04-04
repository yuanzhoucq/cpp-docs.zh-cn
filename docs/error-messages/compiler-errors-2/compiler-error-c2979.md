---
title: 编译器错误 C2979
ms.date: 11/04/2016
f1_keywords:
- C2979
helpviewer_keywords:
- C2979
ms.assetid: 98bd9043-ec44-451e-a482-3a8e35fc7464
ms.openlocfilehash: e9b0af0d17ef57f19e051165b16632e3180159cd
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767049"
---
# <a name="compiler-error-c2979"></a>编译器错误 C2979

泛型中不支持显式专用化

未正确声明泛型类。  请参阅[泛型](../../extensions/generics-cpp-component-extensions.md)有关详细信息。

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
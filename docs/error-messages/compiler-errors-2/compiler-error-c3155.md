---
title: 编译器错误 C3155
ms.date: 11/04/2016
f1_keywords:
- C3155
helpviewer_keywords:
- C3155
ms.assetid: b04a42e1-64e7-40f8-81fe-c7945348b2cf
ms.openlocfilehash: ccbe96075a22ef67d7ebd1f2998b42820bbc79f9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745897"
---
# <a name="compiler-error-c3155"></a>编译器错误 C3155

属性索引器中不允许使用特性

未正确声明索引属性。 有关详细信息，请参阅[如何：在/cli 中C++使用属性](../../dotnet/how-to-use-properties-in-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C3155。

```cpp
// C3155.cpp
// compile with: /clr /c
using namespace System;
ref struct R {
   property int F[[ParamArray] int] {   // C3155
   // try the following line instead
   // property int F[ int] {   // OK
      int get(int i) {
         return 0;
      }
   }
};
```

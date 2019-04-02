---
title: 编译器错误 C3895
ms.date: 11/04/2016
f1_keywords:
- C3895
helpviewer_keywords:
- C3895
ms.assetid: 771b9fe5-d6d4-4297-bf57-e2f857722155
ms.openlocfilehash: c4b1cad9ef48f1f16b411aab46e1bb9285d69ff3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768389"
---
# <a name="compiler-error-c3895"></a>编译器错误 C3895

var： 不能为 volatile 类型的数据成员

某些类型的数据成员，例如[文字](../../extensions/literal-cpp-component-extensions.md)或[initonly](../../dotnet/initonly-cpp-cli.md)，不能为[易失性](../../cpp/volatile-cpp.md)。

下面的示例生成 C3895:

```
// C3895.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   volatile int data_var2;   // C3895
};
```
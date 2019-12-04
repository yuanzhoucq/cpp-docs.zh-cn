---
title: 编译器错误 C3895
ms.date: 11/04/2016
f1_keywords:
- C3895
helpviewer_keywords:
- C3895
ms.assetid: 771b9fe5-d6d4-4297-bf57-e2f857722155
ms.openlocfilehash: 633ffa86bce3579adb808dbba34127bb6f0665c9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749407"
---
# <a name="compiler-error-c3895"></a>编译器错误 C3895

"var"：类型数据成员不能是 "volatile"

某些类型的数据成员（例如[文本](../../extensions/literal-cpp-component-extensions.md)或[initonly](../../dotnet/initonly-cpp-cli.md)）不能是[可变](../../cpp/volatile-cpp.md)的。

下面的示例生成 C3895：

```cpp
// C3895.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   volatile int data_var2;   // C3895
};
```

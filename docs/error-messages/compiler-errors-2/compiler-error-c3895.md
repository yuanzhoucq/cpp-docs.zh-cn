---
title: 编译器错误 C3895
ms.date: 11/04/2016
f1_keywords:
- C3895
helpviewer_keywords:
- C3895
ms.assetid: 771b9fe5-d6d4-4297-bf57-e2f857722155
ms.openlocfilehash: 61dd280caa3c8c9b28dd77ecab2ed50ab9532d4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501278"
---
# <a name="compiler-error-c3895"></a>编译器错误 C3895

var： 不能为 volatile 类型的数据成员

某些类型的数据成员，例如[文字](../../windows/literal-cpp-component-extensions.md)或[initonly](../../dotnet/initonly-cpp-cli.md)，不能为[易失性](../../cpp/volatile-cpp.md)。

下面的示例生成 C3895:

```
// C3895.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   volatile int data_var2;   // C3895
};
```
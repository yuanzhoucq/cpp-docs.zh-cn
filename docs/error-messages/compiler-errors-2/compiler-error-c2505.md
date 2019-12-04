---
title: 编译器错误 C2505
ms.date: 11/04/2016
f1_keywords:
- C2505
helpviewer_keywords:
- C2505
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
ms.openlocfilehash: 94a6f180c93839646d771509145b2f65a00780fd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746859"
---
# <a name="compiler-error-c2505"></a>编译器错误 C2505

"symbol"： "__declspec （修饰符）" 只能应用于全局对象或静态数据成员的声明或定义

在函数中使用了仅用于全局范围的 `__declspec` 修饰符。

有关详细信息，请参见 [应用程序域](../../cpp/appdomain.md) 和 [过程](../../cpp/process.md)。

下面的示例生成 C2505：

```cpp
// C2505.cpp
// compile with: /clr

// OK
__declspec(process) int ii;
__declspec(appdomain) int jj;

int main() {
   __declspec(process) int i;   // C2505
   __declspec(appdomain) int j;   // C2505
}
```

---
title: 编译器错误 C2728
ms.date: 11/04/2016
f1_keywords:
- C2728
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
ms.openlocfilehash: 3e3584d5e9166bb57e3be56e33f0198cacace7c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615171"
---
# <a name="compiler-error-c2728"></a>编译器错误 C2728

“type”：本机数组不能包含此类型

数组创建语法用于创建托管对象或 WinRT 对象的数组。 不能使用本机数组语法创建托管对象或 WinRT 对象的数组。

有关详细信息，请参阅 [数组](../../windows/arrays-cpp-component-extensions.md)。

以下示例将生成 C2728，并演示如何修复此错误：

```
// C2728.cpp
// compile with: /clr

int main() {
   int^ arr[5];   // C2728

   // try the following line instead
   array<int>^arr2;
}
```

---
title: 编译器警告（等级 4）C4324
ms.date: 11/04/2016
f1_keywords:
- C4324
helpviewer_keywords:
- C4324
ms.assetid: 420fa929-d9c0-40b4-8808-2d8ad3ca8090
ms.openlocfilehash: 696f53dff6398555355ca3a58e25d2c6d64eaaab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508350"
---
# <a name="compiler-warning-level-4-c4324"></a>编译器警告（等级 4）C4324

struct_name： 由于 __declspec(align())，结构被填充

因为指定的填充已添加的一种结构末尾[__declspec （align)](../../cpp/align-cpp.md)值。

例如，下面的代码生成 C4324:

```
// C4324.cpp
// compile with: /W4
struct __declspec(align(32)) A
{
   char a;
};   // C4324

int main()
{
}
```
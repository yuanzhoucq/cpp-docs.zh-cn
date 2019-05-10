---
title: 编译器警告（等级 4）C4127
ms.date: 09/13/2018
f1_keywords:
- C4127
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
ms.openlocfilehash: 7f1e23d15d8daa126987278611cb5a85a5a36fc9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401303"
---
# <a name="compiler-warning-level-4-c4127"></a>编译器警告（等级 4）C4127

> 条件表达式是常量

## <a name="remarks"></a>备注

控制表达式**如果**语句或**虽然**循环计算结果为常量。 由于其常见的惯用使用情况，从 Visual Studio 2015 update 3，如 1 常用常数或 **，则返回 true**不触发此警告，除非它们是在表达式中操作的结果。

如果的控制表达式的**虽然**循环是一个常量，因为在中间退出循环，请考虑更换**虽然**循环，并**为**循环。 可以省略初始化、 终止测试和循环增量**有关**循环中，这会导致循环是无限的就像`while(1)`，并可以从正文中退出循环**为**语句。

## <a name="example"></a>示例

下面的示例演示两种方式 C4127 生成的并演示如何使用 for 循环，以避免出现警告：

```cpp
// C4127.cpp
// compile with: /W4
#include <stdio.h>
int main() {
   if (true) {}           // OK in VS2015 update 3 and later
   if (1 == 1) {}         // C4127
   while (42) { break; }  // C4127

   // OK
   for ( ; ; ) {
      printf("test\n");
      break;
   }
}
```
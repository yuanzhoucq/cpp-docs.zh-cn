---
title: 编译器警告（等级 4）C4127
ms.date: 10/16/2019
f1_keywords:
- C4127
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
ms.openlocfilehash: 52a966bb321226058afbf4667a4192e4e814f0a1
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075859"
---
# <a name="compiler-warning-level-4-c4127"></a>编译器警告（等级 4）C4127

> 条件表达式是常量

## <a name="remarks"></a>备注

**If**语句或**while**循环的控制表达式的计算结果为常量。 由于其常见的惯用用法，从 Visual Studio 2015 update 3 开始，普通常量（例如1或**true** ）不会触发警告，除非它们是表达式中操作的结果。

如果**while**循环的控制表达式是常量，因为循环在中间退出，请考虑将**while**循环替换**为 for**循环。 您可以省略**for**循环的初始化、终止测试和循环增量，这将导致循环无限，就像 `while(1)`一样，您可以从**for**语句的主体退出循环。

## <a name="example"></a>示例

下面的示例演示了两种生成 C4127 的方式，并演示了如何使用 for 循环来避免此警告：

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

当编译时常量用于条件表达式时，也会生成此警告：

```cpp
#include <string>

using namespace std;

template<size_t S, class T>
void MyFunc()
{
   if (sizeof(T) >= S) // C4127. "Consider using 'if constexpr' statement instead"
   {
   }
}

class Foo
{
   int i;
   string s;
};

int main()
{
   Foo f;
   MyFunc<4, Foo>();
}
```
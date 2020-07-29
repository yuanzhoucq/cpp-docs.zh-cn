---
title: return 语句 (C++)
ms.date: 11/04/2016
f1_keywords:
- return_cpp
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
ms.openlocfilehash: 6a1ed4f374f133abd0233826d1b58896d49576cf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225860"
---
# <a name="return-statement-c"></a>return 语句 (C++)

终止函数的执行并返回对调用函数的控制（或对操作系统的控制，如果您从 `main` 函数转移控制）。 紧接在调用之后在调用函数中恢复执行。

## <a name="syntax"></a>语法

```
return [expression];
```

## <a name="remarks"></a>备注

`expression` 子句（如果存在）将转换为函数声明中指定的类型，就像正在执行初始化一样。 从表达式的类型到函数类型的转换 **`return`** 可创建临时对象。 有关创建临时内存的方式和时间的详细信息，请参阅[临时对象](../cpp/temporary-objects.md)。

`expression` 子句的值将返回调用函数。 如果省略该表达式，则函数的返回值是不确定的。 构造函数、析构函数以及类型的函数 **`void`** 不能在语句中指定表达式 **`return`** 。 所有其他类型的函数必须在语句中指定表达式 **`return`** 。

当控制流退出包含函数定义的块时，结果与未执行表达式的语句的结果相同 **`return`** 。 这对于声明为返回值的函数无效。

函数可以包含任意数量的 **`return`** 语句。

下面的示例使用带有语句的表达式 **`return`** 来获取两个整数中的最大值。

## <a name="example"></a>示例

```cpp
// return_statement2.cpp
#include <stdio.h>

int max ( int a, int b )
{
   return ( a > b ? a : b );
}

int main()
{
    int nOne = 5;
    int nTwo = 7;

    printf_s("\n%d is bigger\n", max( nOne, nTwo ));
}
```

## <a name="see-also"></a>另请参阅

[跳转语句](../cpp/jump-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)

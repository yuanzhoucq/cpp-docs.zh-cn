---
title: return 语句 (C++)
ms.date: 11/04/2016
f1_keywords:
- return_cpp
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
ms.openlocfilehash: c8ea796ab40a2090ed9853377f7c9415914bc0e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178977"
---
# <a name="return-statement-c"></a>return 语句 (C++)

终止函数的执行并返回对调用函数的控制（或对操作系统的控制，如果您从 `main` 函数转移控制）。 紧接在调用之后在调用函数中恢复执行。

## <a name="syntax"></a>语法

```
return [expression];
```

## <a name="remarks"></a>备注

`expression` 子句（如果存在）将转换为函数声明中指定的类型，就像正在执行初始化一样。 从表达式的类型到函数的**返回**类型的转换可创建临时对象。 有关创建临时内存的方式和时间的详细信息，请参阅[临时对象](../cpp/temporary-objects.md)。

`expression` 子句的值将返回调用函数。 如果省略该表达式，则函数的返回值是不确定的。 构造函数、析构函数和**void**类型的函数不能在**return**语句中指定表达式。 所有其他类型的函数必须在**return**语句中指定表达式。

当控制流退出包含函数定义的块时，结果与未执行表达式的**return**语句的结果相同。 这对于声明为返回值的函数无效。

函数可以包含任意数量的**return**语句。

下面的示例使用带有**return**语句的表达式来获取两个整数中的最大值。

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

---
title: return 语句 (C++)
ms.date: 11/04/2016
f1_keywords:
- return_cpp
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
ms.openlocfilehash: 47bf9c50a2da039b0ffa074796a768290b732bb3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507183"
---
# <a name="return-statement-c"></a>return 语句 (C++)

终止函数的执行并返回对调用函数的控制（或对操作系统的控制，如果您从 `main` 函数转移控制）。 紧接在调用之后在调用函数中恢复执行。

## <a name="syntax"></a>语法

```
return [expression];
```

## <a name="remarks"></a>备注

`expression` 子句（如果存在）将转换为函数声明中指定的类型，就像正在执行初始化一样。 从表达式的类型转换**返回**函数类型可以创建临时对象。 有关如何以及何时创建临时内存的详细信息，请参阅[临时对象](../cpp/temporary-objects.md)。

`expression` 子句的值将返回调用函数。 如果省略该表达式，则函数的返回值是不确定的。 构造函数和析构函数和类型的函数**void**，不能指定在表达式**返回**语句。 所有其他类型的函数必须指定的表达式中**返回**语句。

因为它将时控制流退出封闭函数定义的块，结果是相同如果**返回**不使用表达式的语句已执行。 这对于声明为返回值的函数无效。

一个函数可以有任意数量的**返回**语句。

下面的示例使用与表达式**返回**语句来获取两个整数的最大值。

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

## <a name="see-also"></a>请参阅

[跳转语句](../cpp/jump-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)
---
title: 递归函数
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], recursive
- function calls, recursive
- functions [C], calling recursively
- recursive function calls
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
ms.openlocfilehash: 8979d386c6fc3415cd50159250db8488cb917cee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199511"
---
# <a name="recursive-functions"></a>递归函数

C 程序中的任何函数都可以以递归方式调用；也就是说，函数可以调用自己。 递归调用的数量受堆栈的大小的限制。 若要了解设置堆栈大小的链接器选项，请参阅 [`/STACK`（堆栈分配）](../build/reference/stack-stack-allocations.md)链接器选项。 每次调用函数时，都会为参数以及 `auto` 和 `register` 变量分配新存储，这样它们在以前未完成的调用中的值就不会被覆盖。 只有从中创建参数的函数的实例才能直接访问该参数。 前面的参数对函数的后续实例不可直接访问。

请注意，使用 `static` 存储声明的变量在每次递归调用时不需要新存储。 它们的存储在程序的生存期内存在。 每次引用此类变量时都将访问相同的存储区域。

## <a name="example"></a>示例

本示例演示了递归调用：

```C
int factorial( int num );      /* Function prototype */

int main()
{
    int result, number;
    .
    .
    .
    result = factorial( number );
}

int factorial( int num )      /* Function definition */
{
    .
    .
    .
    if ( ( num > 0 ) || ( num <= 10 ) )
        return( num * factorial( num - 1 ) );
}
```

## <a name="see-also"></a>请参阅

[函数调用](../c-language/function-calls.md)

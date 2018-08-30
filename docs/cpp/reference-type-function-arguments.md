---
title: 引用类型函数自变量 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- functions [C++], paramters
- function parameters [C++], reference-type
- function arguments [C++], reference-type
- passing parameters [C++], reference-type arguments
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 042f609988a87beb8a990405e0426405bc874128
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209746"
---
# <a name="reference-type-function-arguments"></a>引用类型函数自变量

向函数传递引用而非大型对象的效率通常更高。 这使编译器能够在保持已用于访问对象的语法的同时传递对象的地址。 请考虑以下使用了 `Date` 结构的示例：

```cpp
// reference_type_function_arguments.cpp
#include <iostream>

struct Date
{
    short Month;
    short Day;
    short Year;
};

// Create a date of the form DDDYYYY (day of year, year)
// from a Date.
long DateOfYear( Date& date )
{
    static int cDaysInMonth[] = {
        31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31
    };
    long dateOfYear = 0;

    // Add in days for months already elapsed.
    for ( int i = 0; i < date.Month - 1; ++i )
        dateOfYear += cDaysInMonth[i];

    // Add in days for this month.
    dateOfYear += date.Day;

    // Check for leap year.
    if ( date.Month > 2 &&
        (( date.Year % 100 != 0 || date.Year % 400 == 0 ) &&
        date.Year % 4 == 0 ))
        dateOfYear++;

    // Add in year.
    dateOfYear *= 10000;
    dateOfYear += date.Year;

    return dateOfYear;
}

int main()
{
    Date date{ 8, 27, 2018 };
    long dateOfYear = DateOfYear(date);
    std::cout << dateOfYear << std::endl;
}
```

上面的代码显示由引用传递的结构的成员访问使用成员选择运算符 (**。**) 而不是指针成员选择运算符 (**->**)。

尽管作为引用类型传递的参数观察到的非指针类型的语法，但它们保留指针类型的一个重要特征： 它们是可修改，除非声明为**const**。 由于上述代码的目的不是修改对象 `date`，因此更合适的函数原型是：

```cpp
long DateOfYear( const Date& date );
```

此原型将确保函数 `DateOfYear` 不会更改其参数。

原型采用引用类型的任何函数可以接受在其原位置相同的类型的对象，因为没有从标准转换*typename*到*typename*  <strong>&</strong>.

## <a name="see-also"></a>请参阅

[参考资料](../cpp/references-cpp.md)<br/>

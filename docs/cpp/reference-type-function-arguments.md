---
title: 引用类型函数自变量 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 83d78aad4285ad711581dbed1c88ef6b9a8a9b24
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="reference-type-function-arguments"></a>引用类型函数自变量
向函数传递引用而非大型对象的效率通常更高。 这使编译器能够在保持已用于访问对象的语法的同时传递对象的地址。 请考虑以下使用了 `Date` 结构的示例：  
  
```  
// reference_type_function_arguments.cpp  
struct Date  
{  
short DayOfWeek;  
short Month;  
short Day;  
short Year;  
};  
  
// Create a Julian date of the form DDDYYYY  
// from a Gregorian date.  
long JulianFromGregorian( Date& GDate )  
{  
static int cDaysInMonth[] = {  
31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31  
   };  
long JDate = 0;  
// Add in days for months already elapsed.  
for ( int i = 0; i < GDate.Month - 1; ++i )  
JDate += cDaysInMonth[i];  
// Add in days for this month.  
JDate += GDate.Day;  
  
// Check for leap year.  
if ( GDate.Year % 100 != 0 && GDate.Year % 4 == 0 )  
JDate++;  
// Add in year.  
JDate *= 10000;  
JDate += GDate.Year;  
  
return JDate;  
}  
  
int main()  
{  
}  
```  
  
 上面的代码显示通过引用传递的结构的成员访问使用成员选择运算符 (**。**) 而不是指针成员选择运算符 (**->**)。  
  
 尽管作为引用类型传递的自变量遵循了非指针类型的语法，但它们仍然保留了指针类型的一个重要特征： 它们是可以修改除非声明为**const**。 由于上述代码的目的不是修改对象 `GDate`，因此更合适的函数原型是：  
  
```  
long JulianFromGregorian( const Date& GDate );  
```  
  
 此原型将确保函数 `JulianFromGregorian` 不会更改其参数。  
  
 任何函数原型采用引用类型可以接受在其位置的相同类型的对象，因为没有从标准转换*typename*到 * typename ***&**。  
  
## <a name="see-also"></a>请参阅  
 [参考资料](../cpp/references-cpp.md)
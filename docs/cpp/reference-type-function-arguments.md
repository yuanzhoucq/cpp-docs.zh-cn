---
title: "引用类型的函数参数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "参数 [C++], 函数"
  - "函数参数, 引用类型"
  - "函数参数, 引用类型"
  - "函数 [C++], 参数"
  - "传递参数, 引用类型参数"
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 引用类型的函数参数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

向函数传递引用而非大型对象的效率通常更高。  这使编译器能够在保持已用于访问对象的语法的同时传递对象的地址。  请考虑以下使用了 `Date` 结构的示例：  
  
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
  
 前面的代码显示通过引用传递的结构的成员是通过成员选择运算符 \(**.**\) 访问的，而不是通过指针成员选择运算符 \(**–\>**\) 访问的。  
  
 尽管作为引用类型传递的参数遵循了非指针类型的语法，但它们仍然保留了指针类型的一个重要特征：除非被声明为 **const**，否则它们是可以修改的。  由于上述代码的目的不是修改对象 `GDate`，因此更合适的函数原型是：  
  
```  
long JulianFromGregorian( const Date& GDate );  
```  
  
 此原型将确保函数 `JulianFromGregorian` 不会更改其参数。  
  
 任何其原型采用引用类型的函数都能接受其所在位置的相同类型的对象，因为存在从 *typename* 到 *typename***&** 的标准转换。  
  
## 请参阅  
 [引用](../cpp/references-cpp.md)
---
title: "return 语句 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- return
- return_cpp
dev_langs:
- C++
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 7474bc55a5c9d2406465a6ee763c19c2e56e1159
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="return-statement-c"></a>return 语句 (C++)
终止函数的执行并返回对调用函数的控制（或对操作系统的控制，如果您从 `main` 函数转移控制）。 紧接在调用之后在调用函数中恢复执行。  
  
## <a name="syntax"></a>语法  
  
```  
return [expression];  
```  
  
## <a name="remarks"></a>备注  
 `expression` 子句（如果存在）将转换为函数声明中指定的类型，就像正在执行初始化一样。 从该类型的表达式到 `return` 类型的函数的转换会创建临时对象。 有关如何以及何时创建临时内存的详细信息，请参阅[临时对象](../cpp/temporary-objects.md)。  
  
 `expression` 子句的值将返回调用函数。 如果省略该表达式，则函数的返回值是不确定的。 构造函数和析构函数和函数类型`void`，不能指定中的表达式`return`语句。 所有其他类型的函数必须在 `return` 语句中指定表达式。  
  
 当控制流退出封闭函数定义的块时，结果将与执行不带表达式的 `return` 语句所获得的结果一样。 这对于声明为返回值的函数无效。  
  
 一个函数可以包含任意数量的 `return` 语句。  
  
 以下示例将一个表达式与 `return` 语句一起使用来获取两个整数中的最大者。  
  
## <a name="example"></a>示例  
  
```  
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
 [跳转语句](../cpp/jump-statements-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)

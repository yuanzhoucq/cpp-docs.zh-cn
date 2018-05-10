---
title: 返回类型 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function return types
- return values [C++], function procedures
- function return types, syntax
- return values [C++]
- data types [C++], function return types
- return keyword [C++], function return types
- functions [C++], return types
ms.assetid: 3e5b8a97-b341-48c5-8be8-8986980ef586
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18d90604ccaebab2d3ed7812835c711d4d56995a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="return-type"></a>返回类型
函数的返回类型建立由该函数返回的值的大小和类型，并与以下语法中的 type-specifier 相对应：  
  
## <a name="syntax"></a>语法  
 function-definition：  
 declaration-specifiers optattribute-seq optdeclarator declaration-list optcompound-statement  
  
 /\* *attribute-seq* 为 Microsoft 专用 */  
  
 *declaration-specifiers*：  
 storage-class-specifier declaration-specifiers opt  
  
 type-specifier declaration-specifiers opt  
  
 type-qualifier declaration-specifiers opt  
  
 *type-specifier*：  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **signed**  
  
 **unsigned**  
  
 *struct-or-union-specifier*  
  
 *enum-specifier*  
  
 *typedef-name*  
  
 type-specifier 可以指定任何基本、结构或联合类型。 如果不包含 type-specifier，则假定返回类型 `int`。  
  
 函数定义中给定的返回类型必须与程序中其他位置的函数声明中的返回类型相匹配。 当执行包含表达式的 `return` 语句时，函数将返回值。 计算该表达式，转换为返回值类型（如果需要）并返回到调用函数的点。 如果使用返回类型 `void` 声明函数，则包含表达式的返回语句会生成警告，并且不计算该表达式。  
  
 以下示例阐释函数返回值。  
  
```  
typedef struct    
{  
    char name[20];  
    int id;  
    long class;  
} STUDENT;  
  
/* Return type is STUDENT: */  
  
STUDENT sortstu( STUDENT a, STUDENT b )  
{  
    return ( (a.id < b.id) ? a : b );  
}  
```  
  
 该示例定义了带 `STUDENT` 声明的 `typedef` 类型并定义了函数 `sortstu` 以具有 `STUDENT` 返回类型。 函数选择并返回其两个结构参数之一。 在对函数的后续调用中，编译器会检查以确保参数类型是 `STUDENT`。  
  
> [!NOTE]
>  通过传递指向结构的指针而不是整个结构来提高效率。  
  
```  
char *smallstr( char s1[], char s2[] )  
{  
    int i;  
  
    i = 0;  
    while ( s1[i] != '\0' && s2[i] != '\0' )  
        i++;  
    if ( s1[i] == '\0' )  
        return ( s1 );  
    else  
        return ( s2 );  
}  
```  
  
 此示例定义了一个返回指向字符数组的指针的函数。 该函数采用两个字符数组（字符串）作为参数，并返回指向两个字符串中较短的一个字符串的指针。 指向数组的指针将指向第一个数组元素并具有其类型；因此，该函数的返回类型是指向类型 `char` 的指针。  
  
 在调用函数之前，您无需使用 `int` 返回类型声明函数，但建议使用原型，以便启用对参数和返回值的正确类型检查。  
  
## <a name="see-also"></a>请参阅  
 [C 函数定义](../c-language/c-function-definitions.md)
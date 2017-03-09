---
title: "sizeof 运算符 (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sizeof
dev_langs:
- C++
helpviewer_keywords:
- sizeof operator
ms.assetid: 70826d03-3451-41e4-bebb-a820ae66d53f
caps.latest.revision: 6
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
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 051f54958d3ba0523d6047f77d7a8217d60bd51c
ms.lasthandoff: 02/24/2017

---
# <a name="sizeof-operator-c"></a>sizeof 运算符 (C)
`sizeof` 运算符提供了存储操作数的类型的对象所需的存储空间量（以字节为单位）。 利用此运算符，你可以避免在程序中指定依赖于计算机的数据大小。  
  
## <a name="syntax"></a>语法  
  
```  
sizeof unary-expression  
sizeof ( type-name )  
```  
  
## <a name="remarks"></a>备注  
操作数是作为 *unary-expression* 或 type-cast 表达式的标识符（即，用括号括起的类型说明符）。 *unary-expression* 不能表示位域对象、不完整类型或函数指示符。 结果是一个无符号整数常量。 标准标头 STDDEF.H 将此类型定义为 **size_t**。  
  
在将 `sizeof` 运算符应用于数组标识符时，结果是整个数组的大小而不是由数组标识符表示的指针的大小。  
  
将 `sizeof` 运算符应用于结构或联合类型名称，或者应用于结构或联合类型的标识符时，结果是结构或联合中的字节数（包括内部和尾部填充）。 此大小可能包括用于在内存边界上对齐结构成员或联合成员的内部和尾部填充。 因此，结果可能不对应于通过将各个成员的存储需求相加计算出的大小。  
  
如果某个未确定大小的数组是结构的最后一个元素，则 `sizeof` 运算符将返回没有该数组的结构的大小。  
  
```  
buffer = calloc(100, sizeof (int) );  
```  
  
此示例使用 `sizeof` 运算符传递 `int` 的大小（因计算机而异）作为名为 `calloc` 的运行时函数的参数。 该函数返回的值存储在 `buffer` 中。  
  
```  
static char *strings[] = {  
      "this is string one",  
      "this is string two",  
      "this is string three",  
   };  
const int string_no = ( sizeof strings ) / ( sizeof strings[0] );   
```  
  
在此示例中，`strings` 是指向 `char` 的指针的数组。 指针的数目是数组中元素的数目，但是未指定。 通过使用 `sizeof` 运算符计算数组中元素的数目，可以轻松确定指针数目。 **const** 整数值 `string_no` 将初始化为此数字。 由于它是 **const** 值，因此 `string_no` 无法修改。  
  
## <a name="see-also"></a>另请参阅  
[C 运算符](c-operators.md)  
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
  

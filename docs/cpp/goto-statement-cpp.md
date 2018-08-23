---
title: goto 语句 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- goto_cpp
dev_langs:
- C++
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38d022cb3b7f2672ffe7dba6a6d9d4952fa21616
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "42572550"
---
# <a name="goto-statement-c"></a>goto 语句 (C++)
**Goto**语句无条件将控制转移到由指定的标识符标记的语句。  
  
## <a name="syntax"></a>语法  
  
```  
goto identifier;  
```  
  
## <a name="remarks"></a>备注  
 由 `identifier` 指定的标记语句必须位于当前函数中。 所有 `identifier` 名称都是内部命名空间的成员，因此不会干扰其他标识符。  
  
 语句标签是仅对有意义**goto**语句; 否则，语句标签将被忽略。 不能重新声明标签。  

一个**goto**语句不允许将控制转移到跳过在该位置中的范围内的任何变量初始化的位置。 下面的示例引发 C2362:

```cpp
int goto_fn(bool b)
{
    if (!b)
    {
        goto exit;  // C2362
    }
    else
    { /*...*/ }

    int error_code = 42;

exit:
    return error_code;
}
```
  
 它是一个良好的编程样式，以使用**中断**，**继续**，并**返回**语句而不是**goto**语句时可能。 但是，由于**中断**语句从只有一个级别的循环中退出，则可能必须使用**goto**语句退出深度嵌套的循环。  
  
 有关标签的详细信息和**goto**语句，请参阅[Labeled 语句](../cpp/labeled-statements.md)。  
  
## <a name="example"></a>示例  
 在此示例中， **goto**语句将控制转移到标记的点`stop`时`i`等于 3。  
  
```cpp  
// goto_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i, j;  
  
    for ( i = 0; i < 10; i++ )  
    {  
        printf_s( "Outer loop executing. i = %d\n", i );  
        for ( j = 0; j < 2; j++ )  
        {  
            printf_s( " Inner loop executing. j = %d\n", j );  
            if ( i == 3 )  
                goto stop;  
        }  
    }  
  
    // This message does not print:   
    printf_s( "Loop exited. i = %d\n", i );  
  
    stop:   
    printf_s( "Jumped to stop. i = %d\n", i );  
}  
```  
  
```Output  
Outer loop executing. i = 0  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 1  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 2  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 3  
 Inner loop executing. j = 0  
Jumped to stop. i = 3  
```  
  
## <a name="see-also"></a>请参阅  
 [跳转语句](../cpp/jump-statements-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)

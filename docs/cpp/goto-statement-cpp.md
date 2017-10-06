---
title: "goto 语句 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- goto_cpp
dev_langs:
- C++
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
caps.latest.revision: 13
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
ms.openlocfilehash: 3bdad97f36902762f34816a04a4fc0c5c0c16856
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="goto-statement-c"></a>goto 语句 (C++)
`goto` 语句无条件地将控制权转移给由指定的标识符标记的语句。  
  
## <a name="syntax"></a>语法  
  
```  
goto identifier;  
```  
  
## <a name="remarks"></a>备注  
 由 `identifier` 指定的标记语句必须位于当前函数中。 所有 `identifier` 名称都是内部命名空间的成员，因此不会干扰其他标识符。  
  
 语句标签仅对 `goto` 语句有意义；其它情况下，语句标签将被忽略。 不能重新声明标签。  
  
 尽可能使用 `break`、`continue` 和 `return` 语句而不是 `goto` 语句是一种好的编程风格。 但是，因为 `break` 语句仅退出循环的一个级别，所以可能必须使用 `goto` 语句退出深度嵌套的循环。  
  
 有关标签的详细信息和`goto`语句，请参阅[Labeled 语句](../cpp/labeled-statements.md)和[goto 语句中使用标签](http://msdn.microsoft.com/en-us/6cd7c31a-9822-4241-8566-f79f51be48fe)。  
  
## <a name="example"></a>示例  
 在此示例中，当 `i` 等于 3 时，`goto` 语句将控制权转移给标记为 `stop` 的点。  
  
```  
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
  
## <a name="see-also"></a>另请参阅  
 [跳转语句](../cpp/jump-statements-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)

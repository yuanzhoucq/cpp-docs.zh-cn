---
title: "函数调用 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls, about function calls
- function calls
ms.assetid: 2cfa897d-3874-4820-933c-e624f75d1712
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c5c314fb66a6bd45d1e9ce22b9d88195dce27b85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="function-calls"></a>函数调用
函数调用是一个用于将控制权和参数（如果有）传递给函数的表达式，格式如下：  
  
 expression (expression-listopt)  
  
 其中 expression 是一个函数名称或者其计算结果为函数地址，而 expression-list 是表达式的列表（以逗号分隔）。 后面这些表达式的值是传递给函数的自变量。 如果函数未返回值，则将其声明为返回 `void` 的函数。  
  
 如果在函数调用之前存在声明，但未提供任何与参数有关的信息，则任何未声明的参数只需进行常用算术转换。  
  
> [!NOTE]
>  函数参数列表中的表达式可以任何顺序进行计算，因此其值可能受其他参数的副作用而更改的参数具有未定义的值。 函数调用运算符定义的序列点仅保证在将控制权传递给所调用函数之前计算参数列表中的所有副作用。 （请注意，在堆栈上推送自变量的顺序是另一回事。）有关详细信息，请参阅[序列点](../c-language/c-sequence-points.md)。  
  
 所有函数调用中的唯一要求是，括号前的表达式的计算结果必须是函数地址。 这意味着可通过任何函数指针表达式调用函数。  
  
## <a name="example"></a>示例  
 此示例说明了通过 `switch` 语句调用的函数调用：  
  
```  
int main()  
{  
    /* Function prototypes */  
  
    long lift( int ), step( int ), drop( int );  
    void work( int number, long (*function)(int i) );  
  
    int select, count;  
    .  
    .  
    .  
    select = 1;  
    switch( select )   
    {  
        case 1: work( count, lift );  
                break;  
  
        case 2: work( count, step );  
                break;  
  
        case 3: work( count, drop );  
                /* Fall through to next case */  
        default:  
                break;  
    }  
}  
  
/* Function definition */  
  
void work( int number, long (*function)(int i) )  
{  
    int i;  
    long j;  
  
    for ( i = j = 0; i < number; i++ )  
            j += ( *function )( i );  
}  
```  
  
 在此示例中，`main` 中的函数调用  
  
```  
work( count, lift );  
```  
  
 将整数变量 `count` 和函数 `lift` 的地址传递给函数 `work`。 请注意，由于函数标识符的计算结果是一个针表达式，因此通过提供函数标识符即可传入函数地址。 若要通过此方式使用函数标识符，必须在使用标识符前先声明或定义函数；否则，将不会识别标识符。 在此示例中，`work` 的原型在 `main` 函数的开头处提供。  
  
 `work` 中的形参 `function` 将声明为指向采用一个 `int` 实参并返回一个 long 值的函数的指针。 参数名称两边需要括号；如果没有括号，声明将返回一个指向 long 值的指针的函数。  
  
 函数 `work` 通过使用以下函数调用来调用 for 循环内的选定函数：  
  
```  
( *function )( i );  
```  
  
 一个参数 `i` 将传递给所调用的参数。  
  
## <a name="see-also"></a>请参阅  
 [函数](../c-language/functions-c.md)
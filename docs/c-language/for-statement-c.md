---
title: "for 语句 (C) |Microsoft 文档"
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
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 13d292cebbb8aa3aa6a65fbc41b8b38934732b5f
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="for-statement-c"></a>for 语句 (C)
使用 **for** 语句可以重复语句或复合语句指定的次数。 在可选条件变为 false 前，**for** 语句的主体将执行零次或多次。 可以在 **for** 语句中使用可选表达式，以便在 **for** 语句的执行期间初始化和更改值。  
  
## <a name="syntax"></a>语法  
 *iteration-statement*:  
 &nbsp;&nbsp;**for** **(** *init-expression*<sub>opt</sub> **;** *cond-expression*<sub>opt</sub> **;** *loop-expression*<sub>opt</sub> **)** *statement*  
  
 **for** 语句的执行将按以下方式继续：  
  
1.  将计算 *init-expression*（如果有）。 这将为循环指定初始化。 对 *init-expression* 的类型没有限制。  
  
2.  将计算 *cond-expression*（如果有）。 此表达式必须具有算法或指针类型。 它在每次迭代前计算。 可能有三个结果：  
  
    -   如果 *cond-expression* 为 **true**（非零），则执行语句，然后计算 *loop-expression*（若有）。 在每次迭代之后，将计算 *loop-expression*。 对其类型没有限制。 副作用将按顺序执行。 该过程随后从计算 *cond-expression* 重新开始。  
  
    -   如果省略了 *cond-expression*，则 *cond-expression* 被视为 true，执行将完全按上一段中所述方式继续。 仅当执行了语句体中的 **break** 或 **return** 语句时，或执行了 **goto**（到 **for** 语句体外的标记语句）时，没有 *cond-expression* 参数的 **for** 语句才会终止。  
  
    -   如果 *cond-expression* 为 **false** (0),，则 **for** 语句的执行将终止，控制权将传递到程序中的下一条语句。  
  
 **for** 语句还会在语句体中执行 **break**、**goto**或 **return** 语句时终止。 **for** 循环中的 **continue** 语句会导致计算 *loop-expression*。 当在 **for** 循环中执行 **break** 语句时，不会计算或执行 *loop-expression*。 以下语句  
  
```  
for( ;; )  
```  
  
 是生成只能与 **break**、**goto** 或 **return** 语句一起退出的无限循环的习惯方法。  
  
## <a name="code"></a>代码  
 以下示例演示了 **for** 语句：  
  
```  
// c_for.c  
int main()  
{  
   char* line = "H e  \tl\tlo World\0";  
   int space = 0;  
   int tab = 0;  
   int i;  
   int max = strlen(line);  
   for (i = 0; i < max; i++ )   
   {  
      if ( line[i] == ' ' )  
      {  
          space++;  
      }  
      if ( line[i] == '\t' )  
      {  
          tab++;  
      }  
   }  
  
   printf("Number of spaces: %i\n", space);  
   printf("Number of tabs: %i\n", tab);  
   return 0;  
}  
```  
  
## <a name="output"></a>输出  
  
```  
Number of spaces: 4  
Number of tabs: 2  
```  
  
## <a name="see-also"></a>另请参阅  
 [语句](../c-language/statements-c.md)

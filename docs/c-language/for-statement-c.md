---
title: for 语句 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
ms.openlocfilehash: df00bcab2f9f9e51a6f37e19670b6cd240fa5cc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233639"
---
# <a name="for-statement-c"></a>for 语句 (C)

使用 **for** 语句可以重复语句或复合语句指定的次数。 在可选条件变为 false 前，**for** 语句的主体将执行零次或多次。 可以在 **for** 语句中使用可选表达式，以便在 **for** 语句的执行期间初始化和更改值。

## <a name="syntax"></a>语法

*iteration-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for** **(** *init-expression*<sub>opt</sub> **;** *cond-expression*<sub>opt</sub> **;** *loop-expression*<sub>opt</sub> **)** *statement*

**for** 语句的执行将按以下方式继续：

1. 将计算 *init-expression*（如果有）。 这将为循环指定初始化。 对 *init-expression* 的类型没有限制。

1. 将计算 *cond-expression*（如果有）。 此表达式必须具有算法或指针类型。 它在每次迭代前计算。 可能有三个结果：

   - 如果 *cond-expression* 为 **true**（非零），则执行语句  ，然后计算 *loop-expression*（若有）。 在每次迭代之后，将计算 *loop-expression*。 对其类型没有限制。 副作用将按顺序执行。 该过程随后从计算 *cond-expression* 重新开始。

   - 如果省略了 *cond-expression*，则 *cond-expression* 被视为 true，执行将完全按上一段中所述方式继续。 仅当执行了语句体中的 **break** 或 **return** 语句时，或执行了 **goto**（到 **for** 语句体外的标记语句）时，没有 *cond-expression* 参数的 **for** 语句才会终止。

   - 如果 *cond-expression* 为 **false** (0),，则 **for** 语句的执行将终止，控制权将传递到程序中的下一条语句。

**for** 语句还会在语句体中执行 **break**、**goto**或 **return** 语句时终止。 **for** 循环中的 **continue** 语句会导致计算 *loop-expression*。 当在 **for** 循环中执行 **break** 语句时，不会计算或执行 *loop-expression*。 以下语句

```C
for( ; ; )
```

是生成只能与 **break**、**goto** 或 **return** 语句一起退出的无限循环的习惯方法。

## <a name="example"></a>示例

以下示例演示了 **for** 语句：

```C
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

## <a name="output"></a>Output

```Output
Number of spaces: 4
Number of tabs: 2
```

## <a name="see-also"></a>请参阅

[语句](../c-language/statements-c.md)

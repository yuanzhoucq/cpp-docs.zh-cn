---
title: for 语句 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
ms.openlocfilehash: 91675fbe15ec6abf5aae4548990d9b4e0703e967
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229722"
---
# <a name="for-statement-c"></a>for 语句 (C)

利用 `for` 语句，可以将语句或复合语句重复执行指定的次数。 执行 `for` 语句的主体零次或多次，直到可选条件变成 false。 可以在 `for` 语句中使用可选表达式，以便在 `for` 语句的执行期间初始化和更改值。

## <a name="syntax"></a>语法

*iteration-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`for` ( init-expression<sub>opt</sub> ; cond-expression<sub>opt</sub> ; loop-expression<sub>opt</sub> ) statement

`for` 语句的执行过程如下：

1. 将计算 *init-expression*（如果有）。 这将为循环指定初始化。 对 *init-expression* 的类型没有限制。

1. 将计算 *cond-expression*（如果有）。 此表达式必须具有算法或指针类型。 它在每次迭代前计算。 可能有三个结果：

   - 如果 cond-expression 为 `true`（非零），则执行语句，然后计算 loop-expression（若有）。 在每次迭代之后，将计算 *loop-expression*。 对其类型没有限制。 副作用将按顺序执行。 该过程随后从计算 *cond-expression* 重新开始。

   - 如果省略了 *cond-expression*，则 *cond-expression* 被视为 true，执行将完全按上一段中所述方式继续。 只有在执行了语句主体中的 `break` 或 `return` 语句时，或只有在执行了 `goto`（转到 `for` 语句主体外的带标签的语句）时，没有 cond-expression 参数的 `for` 语句才会终止。

   - 如果 cond-expression 为 `false` (0)，则 `for` 语句的执行终止，并将控制权传递给程序中的下一个语句。

在执行了语句主体中的 `break`、`goto` 或 `return` 语句时，`for` 语句也会终止。 `for` 循环中的 `continue` 语句会导致计算 loop-expression。 当 `break` 语句在 `for` 循环中执行时，不会计算或执行 loop-expression。 以下语句

```C
for( ; ; )
```

是生成只能通过 `break`、`goto` 或 `return` 语句退出的无限循环的惯用方法。

## <a name="example"></a>示例

下面的示例展示了 `for` 语句：

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

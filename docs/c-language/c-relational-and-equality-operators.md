---
title: C 关系和相等运算符
ms.date: 10/18/2018
helpviewer_keywords:
- relational operators, syntax
- equality operator
- operators [C], equality
- equality operator, syntax
- operators [C], relational
ms.assetid: c89a3815-a65e-4e0d-8333-0e8dc7fdb30b
ms.openlocfilehash: 9ae5a31b5f4b81876d2fe518635a9766d2b5323c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227941"
---
# <a name="c-relational-and-equality-operators"></a>C 关系和相等运算符

二元关系运算符和相等运算符将其第一个操作数与其第二个操作数进行比较以测试指定关系的有效性。 如果测试的关系为 true，则关系表达式的结果为 1；如果测试的关系为 false，则关系表达式的结果为 0。 结果的类型为 `int`。

**语法**

*relational-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **&lt;** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **>** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **&lt;=** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **>=** *shift-expression*

*equality-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression* **==** *relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression* **!=** *relational-expression*

关系运算符和相等运算符测试以下关系：

|运算符|测试的关系|
|--------------|-------------------------|
|**&lt;**|第一个操作数小于第二个操作数|
|**>**|第一个操作数大于第二个操作数|
|**&lt;=**|第一个操作数小于或等于第二个操作数|
|**>=**|第一个操作数大于或等于第二个操作数|
|**==**|第一个操作数等于第二个操作数|
|**!=**|第一个操作数不等于第二个操作数|

上面的列表中的前四个运算符的优先级高于相等运算符（`==` 和 `!=`）的优先级。 请参阅表 [C 运算符的优先级和关联性](../c-language/precedence-and-order-of-evaluation.md)中的优先级信息。

操作数可以具有整型、浮点型或指针类型。 操作数的类型可以不同。 关系运算符对整型和浮点型的操作数执行常用算术转换。 此外，您可以使用以下操作数类型与关系运算符和相等运算符的组合：

- 任意关系运算符或相等运算符的操作数可以是指向同一类型的指针。 对于相等 (`==`) 运算符和不相等（`!=`）运算符，比较的结果指示两个指针是否对相同的内存位置寻址。 对于其他关系运算符（\<**, **>、\<**=, and **>=），比较的结果指明了所指向的对象的两个内存地址的相对位置。 关系运算符仅比较偏移量。

   仅为同一个对象的部分定义指针比较。 如果指针引用数组的成员，则比较与相应下标的比较是等效的。 第一个数组元素的地址“少于”最后一个元素的地址。 对于结构，指向稍后声明的结构成员的指针“大于”指向之前在结构中声明的成员的指针。 指向同一联合的成员的指针是相等的。

- 指针值可以与常量值 0 进行比较以确定相等 (`==`) 或不相等 (`!=`)。 值为 0 的指针称为“null”指针；即，它不指向有效的内存位置。

- 相等运算符遵循与关系运算符相同的规则，但允许执行更多可能的运算，即可以将指针与值为 0 的常数整型表达式或指向 `void` 的指针进行比较。 如果两个指针都是 null 指针，则它们的比较结果相等。 相等运算符比较段和偏移量。

## <a name="examples"></a>示例

下面的示例阐释了关系运算符和相等运算符。

```C
int x = 0, y = 0;
if ( x < y )
```

由于 `x` 和 `y` 相等，因此该示例中的表达式会生成值 0。

```C
char array[10];
char *p;

for ( p = array; p < &array[10]; p++ )
    *p = '\0';
```

此示例中的片段将 `array` 的每个元素设置为 null 字符常量。

```C
enum color { red, white, green } col;
   .
   .
   .
   if ( col == red )
   .
   .
   .
```

这些语句声明带标记 `col` 的名为 `color` 的枚举变量。 在任何时候，变量可以包含整数值 0、1 或 2，这表示枚举集 `color` 的某个元素：分别为红色、白色或绿色。 如果在执行 `if` 语句时 `col` 包含 0，则任何依赖 `if` 的语句都将被执行。

## <a name="see-also"></a>请参阅

[关系运算符：\<, >、\<=, and >=](../cpp/relational-operators-equal-and-equal.md)<br/>
[相等运算符：== 和 !=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)

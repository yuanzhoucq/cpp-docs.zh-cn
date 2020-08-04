---
title: C 逻辑运算符
ms.date: 06/14/2018
helpviewer_keywords:
- logical operators, expression sequence points
- logical operators, C
- logical AND operator
- '|| operator'
- operators [C], logical
- short-circuit evaluation
- '&& operator'
- logical OR operator
ms.assetid: c0a4e766-ad56-4300-bf76-b28dc0e19b43
ms.openlocfilehash: 8f59ad927dd8ee62dbfc80fd238677bf1b646f9c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227993"
---
# <a name="c-logical-operators"></a>C 逻辑运算符

逻辑运算符执行 logical-AND (&&  ) 和 logical-OR ||(  ) 运算。

## <a name="syntax"></a>语法

*logical-AND-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;inclusive-OR-expression<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-AND-expression*  **&&**  *inclusive-OR-expression*

*logical-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;logical-AND-expression<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*  **&#124;&#124;**  *logical-AND-expression*

## <a name="remarks"></a>备注

逻辑运算符不执行常用算术转换。 相反，它们根据其等效性为 0 计算每个操作数。 逻辑运算的结果不是 0 就是 1。 结果的类型为 `int`。

C 逻辑运算符如下所述：

|运算符|描述|
|--------------|-----------------|
|**&&**|如果两个操作数具有非零值，则逻辑“与”运算符产生值 1。 如果其中一个操作数等于 0，则结果为 0。 如果逻辑“与”运算的第一个操作数等于 0，则不会计算第二个操作数。|
|**&#124;&#124;**|逻辑“或”运算符对其操作数执行“与或”运算。 如果两个操作数的值均为 0，则结果为 0。 如果其中一个操作数具有非零值，则结果为 1。 如果逻辑“或”运算的第一个操作数具有非零值，则不会计算第二个操作数。|

逻辑“与”和逻辑“或”表达式的操作数从左到右进行计算。 如果第一个操作数的值足以确定运算的结果，则不会计算第二个操作数。 这称作“短路计算”。 第一个操作数后有一个序列点。 有关详细信息，请参阅[序列点](../c-language/c-sequence-points.md)。

## <a name="examples"></a>示例

下面的示例演示了逻辑运算符：

```C
int w, x, y, z;

if ( x < y && y < z )
    printf( "x is less than z\n" );
```

在此示例中，如果 `x` 小于 `y` 且 `y` 小于 `z`，则调用 printf  函数以输出消息。 如果 `x` 大于 `y`，则不会计算第二个操作数 (`y < z`) 且不会输出任何内容。 请注意，如果第二个操作数具有由于某个其他原因而产生的副作用，这可能会导致出现问题。

```C
printf( "%d" , (x == w || x == y || x == z) );
```

在此示例中，如果 `x` 与 `w`、`y` 或 `z` 相等，则 printf  函数的第二个参数的计算结果将为 true，并输出值 1。 否则，它的计算结果将为 false，并打印值 0。 只要其中一个条件的计算结果为 true，计算便会停止。

## <a name="see-also"></a>请参阅

- [逻辑 AND 运算符：&&](../cpp/logical-and-operator-amp-amp.md)
- [逻辑“或”运算符：&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)

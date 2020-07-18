---
title: MASM 运算符引用
ms.date: 07/15/2020
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: c29b173a1dcf29c297e41f136044599fbd5218a5
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446458"
---
# <a name="masm-operators-reference"></a>MASM 运算符引用

## <a name="arithmetic"></a>算术

:::row:::
   :::column span="":::
      [`*`乘](operator-multiply.md)<br/>[`+`把](operator-add.md)<br/>[`-`（减或取反）](operator-subtract-2.md)
   :::column-end:::
   :::column span="":::
      [`.`定义域](operator-dot.md)<br/>[`/`拆分](operator-subtract-1.md)
   :::column-end:::
   :::column span="":::
      [`[]`编入](operator-brackets.md)<br/>[`MOD`剩下](operator-mod.md)
   :::column-end:::
:::row-end:::

## <a name="control-flow"></a>控制流

:::row:::
   :::column span="":::
      [`!`（运行时逻辑非）](operator-logical-not-masm-run-time.md)<br/>[`!=`（运行时不等于）](operator-not-equal-masm.md)<br/>[`||`（运行时逻辑或）](operator-logical-or.md)<br/>[`&&`（运行时逻辑与）](operator-logical-and-masm-run-time.md)<br/>[`<`（运行时小于）](operator-less-than-masm-run-time.md)
   :::column-end:::
   :::column span="":::
      [`<=`（运行时小于或等于）](operator-less-or-equal-masm-run-time.md)<br/>[`==`（运行时相等）](operator-equal-masm-run-time.md)<br/>[`>`（运行时大于）](operator-greater-than-masm-run-time.md)<br/>[`>=`（运行时大于或等于）](operator-greater-or-equal-masm-run-time.md)<br/>[`&`（运行时位与）](operator-bitwise-and.md)
   :::column-end:::
   :::column span="":::
      [`CARRY?`（运行时执行测试）](operator-carry-q.md)<br/>[`OVERFLOW?`（运行时溢出测试）](operator-overflow-q.md)<br/>[`PARITY?`（运行时奇偶测试）](operator-parity-q.md)<br/>[`SIGN?`（运行时签名测试）](operator-sign-q.md)<br/>[`ZERO?`（运行时零测试）](operator-zero-q.md)
   :::column-end:::
:::row-end:::

## <a name="logical-and-shift"></a>逻辑与移位

:::row:::
   :::column span="":::
      [`AND`（位与）](operator-and.md)<br/>[`NOT`（位非）](operator-not.md)
   :::column-end:::
   :::column span="":::
      [`OR`（位或）](operator-or.md)<br/>[`SHL`（向左移动位）](operator-shl.md)
   :::column-end:::
   :::column span="":::
      [`SHR`（向右移位）](operator-shr.md)<br/>[`XOR`（位异或）](operator-xor.md)
   :::column-end:::
:::row-end:::

## <a name="macro"></a>宏

:::row:::
   :::column span="":::
      [`!`（字符文本）](operator-logical-not-masm.md)<br/>[`%`（视为文本）](operator-percent.md)
   :::column-end:::
   :::column span="":::
      [`;;`（视为注释）](operator-semicolons.md)<br/>[`< >`（视为一个文本）](operator-literal.md)
   :::column-end:::
   :::column span="":::
      [`& &`（替换参数值）](operator-logical-and-masm.md)
   :::column-end:::
:::row-end:::

## <a name="miscellaneous"></a>杂项

:::row:::
   :::column span="":::
      [`' '`（视为 string）](operator-single-quote.md)<br/>[`" "`（视为 string）](operator-double-quote.md)<br/>`:`（本地标签定义）
   :::column-end:::
   :::column span="":::
      `::`（寄存器段和偏移量）<br/>`::`（全局标签定义）
   :::column-end:::
   :::column span="":::
      [`;`（视为注释）](operator-semicolon.md)<br/>[`DUP`（重复声明）](operator-dup.md)
   :::column-end:::
:::row-end:::

## <a name="record"></a>Record

:::row:::
   :::column span="":::
      [`MASK`（获取记录或字段位掩码）](operator-mask.md)
   :::column-end:::
   :::column span="2":::
      [`WIDTH`（获取记录或字段宽度）](operator-width.md)
   :::column-end:::
:::row-end:::

## <a name="relational"></a>关系

:::row:::
   :::column span="":::
      [`EQ`=](operator-eq.md)<br/>[`GE`（大于或等于）](operator-ge.md)
   :::column-end:::
   :::column span="":::
      [`GT`（大于）](operator-gt.md)<br/>[`LE`（小于或等于）](operator-le.md)
   :::column-end:::
   :::column span="":::
      [`LT`（小于）](operator-lt.md)<br/>[`NE`（不等于）](operator-ne.md)
   :::column-end:::
:::row-end:::

## <a name="segment"></a>段

:::row:::
   :::column span="":::
      [`:`（段重写）](operator-colon.md)<br/>`::`（寄存器段和偏移量）<br/>[`IMAGEREL`（图像相对偏移量）](operator-imagerel.md)
   :::column-end:::
   :::column span="":::
      [`LROFFSET`（加载器解析偏移量）](operator-lroffset.md)<br/>[`OFFSET`（段相对偏移量）](operator-offset.md)
   :::column-end:::
   :::column span="":::
      [`SECTIONREL`（节相对偏移量）](operator-sectionrel.md)<br/>[`SEG`（获取段）](operator-seg.md)
   :::column-end:::
:::row-end:::

## <a name="type"></a>类型

:::row:::
   :::column span="":::
      [`HIGH`（高8位，最低16位）](operator-high.md)<br/>[`HIGH32`（64位高32位）](operator-high32.md)<br/>[`HIGHWORD`（高16位，最低32位）](operator-highword.md)<br/>[`LENGTH`（数组中的元素数）](operator-length.md)<br/>[`LENGTHOF`（数组中的元素数）](operator-lengthof.md)<br/>[`LOW`（低8位）](operator-low.md)
   :::column-end:::
   :::column span="":::
      [`LOW32`（低32位）](operator-low32.md)<br/>[`LOWWORD`（低16位）](operator-lowword.md)<br/>[`OPATTR`（获取参数类型信息）](operator-opattr.md)<br/>[`PTR`（指向或类型的指针）](operator-ptr.md)<br/>[`SHORT`（标记短标签类型）](operator-short.md)
   :::column-end:::
   :::column span="":::
      [`SIZE`（类型或变量的大小）](operator-size.md)<br/>[`SIZEOF`（类型或变量的大小）](operator-sizeof.md)<br/>[`THIS`（当前位置）](operator-this.md)<br/>[`TYPE`（获取表达式类型）](operator-type.md)<br/>[`.TYPE`（获取参数类型信息）](operator-dot-type.md)
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>请参阅

[Microsoft 宏汇编程序参考](microsoft-macro-assembler-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)

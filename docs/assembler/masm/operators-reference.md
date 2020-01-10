---
title: MASM 运算符引用
ms.date: 12/17/2019
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: c0059ab1b0204b79e040d18bd5aa88145775ebcd
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318756"
---
# <a name="masm-operators-reference"></a>MASM 运算符引用

## <a name="arithmetic"></a>算术

||||
|-|-|-|
|[* （乘）](operator-multiply.md)|[+ （添加）](operator-add.md)|[-（减或取反）](operator-subtract-2.md)|
|[.定义域](operator-dot.md)|[/ (divide)](operator-subtract-1.md)|[&#91;&#93;编入](operator-brackets.md)|
|[MOD （余数）](operator-mod.md)|||

## <a name="control-flow"></a>控制流

||||
|-|-|-|
|[\! （运行时逻辑非）](operator-logical-not-masm-run-time.md)|[\!= （运行时不等于）](operator-not-equal-masm.md)|[&#124;&#124;（运行时逻辑或）](operator-logical-or.md)|
|[& & （运行时逻辑与）](operator-logical-and-masm-run-time.md)|[< （运行时小于）](operator-less-than-masm-run-time.md)|[\<= （运行时小于或等于）](operator-less-or-equal-masm-run-time.md)|
|[= = （运行时相等）](operator-equal-masm-run-time.md)|[> （运行时大于）](operator-greater-than-masm-run-time.md)|[> = （运行时大于或等于）](operator-greater-or-equal-masm-run-time.md)|
|[& （运行时位与）](operator-bitwise-and.md)|||
|[送修?（运行时执行测试）](operator-carry-q.md)|[超出?（运行时溢出测试）](operator-overflow-q.md)|[性?（运行时奇偶测试）](operator-parity-q.md)|
|[表明?（运行时签名测试）](operator-sign-q.md)|[无?（运行时零测试）](operator-zero-q.md)||

## <a name="logical-and-shift"></a>逻辑与移位

||||
|-|-|-|
|[AND （位与）](operator-and.md)|[不（位非）](operator-not.md)|[或（位或）](operator-or.md)|
|[SHL （向左移动位）](operator-shl.md)|[SHR （向右移位）](operator-shr.md)|[XOR （位异或）](operator-xor.md)|

## <a name="macro"></a>宏

||||
|-|-|-|
|[\! （字符文本）](operator-logical-not-masm.md)|[% （视为文本）](operator-percent.md)||
|[;;（视为注释）](operator-semicolons.md)|[&lt; &gt; （视为一个文本）](operator-literal.md)|[& & （替换参数值）](operator-logical-and-masm.md)|

## <a name="miscellaneous"></a>其他

||||
|-|-|-|
|["" （视为字符串）](operator-single-quote.md)|["" （视为字符串）](operator-double-quote.md)||
|：（本地标签定义）|：：（寄存器段和偏移量）|：：（全局标签定义）|
|[;（视为注释）](operator-semicolon.md)|[DUP （重复声明）](operator-dup.md)||

## <a name="record"></a>记录

|||
|-|-|
|[掩码（获取记录或字段位掩码）](operator-mask.md)|[WIDTH （获取记录或字段宽度）](operator-width.md)|

## <a name="relational"></a>关系

||||
|-|-|-|
|[EQ （等于）](operator-eq.md)|[GE （大于或等于）](operator-ge.md)|[G t （大于）](operator-gt.md)|
|[LE （小于或等于）](operator-le.md)|[LT （小于）](operator-lt.md)|[NE （不等于）](operator-ne.md)|

## <a name="segment"></a>细分市场

|||
|-|-|
|[：（段替代）](operator-colon.md)|：：（寄存器段和偏移量）|
|[IMAGEREL （图像相对偏移量）](operator-imagerel.md)|[LROFFSET （加载器解析的偏移量）](operator-lroffset.md)|
|[偏移量（段相对偏移量）](operator-offset.md)|[SECTIONREL （节相对偏移量）](operator-sectionrel.md)|
|[SEG （获取段）](operator-seg.md)||

## <a name="type"></a>类型

||||
|-|-|-|
|[HIGH （高8位，最低16位）](operator-high.md)|[HIGH32 （64位高32位）](operator-high32.md)|[HIGHWORD （高16位，最低32位）](operator-highword.md)|
|[长度（数组中的元素数）](operator-length.md)|[LENGTHOF （数组中的元素数）](operator-lengthof.md)|[低（低8位）](operator-low.md)|
|[LOW32 （低32位）](operator-low32.md)|[LOWWORD （低16位）](operator-lowword.md)|[OPATTR （获取参数类型信息）](operator-opattr.md)|
|[PTR （指向或类型的指针）](operator-ptr.md)|[SHORT （标记 short 标签类型）](operator-short.md)|[大小（类型或变量的大小）](operator-size.md)|
|[SIZEOF （类型或变量的大小）](operator-sizeof.md)|[此（当前位置）](operator-this.md)|[类型（获取表达式类型）](operator-type.md)|
|[.类型（获取参数类型信息）](operator-dot-type.md)|||

## <a name="see-also"></a>另请参阅

[Microsoft 宏汇编程序参考](microsoft-macro-assembler-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)

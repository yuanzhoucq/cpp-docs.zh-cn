---
title: MASM 运算符参考
ms.date: 08/30/2018
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: cb97c5dcb640b8d8592d842afd7dbb8cf9d0852c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430454"
---
# <a name="masm-operators-reference"></a>MASM 运算符参考

## <a name="arithmetic"></a>算术运算

||||
|-|-|-|
|[* （乘）](operator-multiply.md)|[+ （加）](operator-add.md)|[-（减法或求反）](operator-subtract-2.md)|
|[.（字段）](operator-dot.md)|[/ （除）](operator-subtract-1.md)|[&#91;&#93;（索引）](operator-brackets.md)|
|[求模 （余数）](operator-mod.md)|||

## <a name="control-flow"></a>控制流

||||
|-|-|-|
|[\! （运行时逻辑非）](operator-logical-not-masm-run-time.md)|[\!= （运行时不等于）](operator-not-equal-masm.md)|[&#124;&#124;(运行时逻辑或)](operator-logical-or.md)|
|[& & (逻辑的运行时和)](operator-logical-and-masm-run-time.md)|[< (运行时内)](operator-less-than-masm-run-time.md)|[\<= （运行时小于或等于）](operator-less-or-equal-masm-run-time.md)|
|[= = （等于运行时）](operator-equal-masm-run-time.md)|[> （大于运行时）](operator-greater-than-masm-run-time.md)|[> = （运行时大于或等于）](operator-greater-or-equal-masm-run-time.md)|
|[& (位运行时和)](operator-bitwise-and.md)|||
|[CARRY？（运行时携带测试）](operator-carry-q.md)|[OVERFLOW？（运行时溢出测试）](operator-overflow-q.md)|[奇偶校验？（运行时的奇偶校验测试）](operator-parity-q.md)|
|[登录？（运行时登录测试）](operator-sign-q.md)|[零？（运行时为零测试）](operator-zero-q.md)||

## <a name="logical-and-shift"></a>逻辑和 Shift

||||
|-|-|-|
|[和 (按位和)](operator-and.md)|[不 （位非）](operator-not.md)|[OR (按位或)](operator-or.md)|
|[SHL (左 shift bits)](operator-shl.md)|[SHR (右 shift bits)](operator-shr.md)|[XOR (位异或)](operator-xor.md)|

## <a name="macro"></a>宏

||||
|-|-|-|
|[\! （字符文本）](operator-logical-not-masm.md)|[%（视为文本）](operator-percent.md)||
|[;;（将视为注释）](operator-semicolons.md)|[&lt; &gt; （将视为一个文本）](operator-literal.md)|[& & （替换参数值）](operator-logical-and-masm.md)|

## <a name="miscellaneous"></a>杂项

||||
|-|-|-|
|[（将作为字符串处理）](operator-single-quote.md)|[""（将作为字符串处理）](operator-double-quote.md)||
|: （本地标签定义)|:: （注册段和偏移量)|:: （全局标签定义)|
|[;（将视为注释）](operator-semicolon.md)|[DUP （重复声明）](operator-dup.md)||

## <a name="record"></a>记录

|||
|-|-|
|[掩码 （获取记录或字段的位掩码）](operator-mask.md)|[宽度 （获取记录或字段的宽度）](operator-width.md)|

## <a name="relational"></a>关系

||||
|-|-|-|
|[EQ （等于）](operator-eq.md)|[GE （大于或等于）](operator-ge.md)|[GT （大于）](operator-gt.md)|
|[LE （小于或等于）](operator-le.md)|[LT （小于）](operator-lt.md)|[NE （不等于）](operator-ne.md)|

## <a name="segment"></a>段

|||
|-|-|
|[: （段重写)](operator-colon.md)|:: （注册段和偏移量)|
|[IMAGEREL （图像相对偏移量）](operator-imagerel.md)|[LROFFSET （加载程序解析偏移量）](operator-lroffset.md)|
|[偏移量 （段相对偏移量）](operator-offset.md)|[SECTIONREL （部分相对偏移量）](operator-sectionrel.md)|
|[SEG （get 段）](operator-seg.md)||

## <a name="type"></a>类型

||||
|-|-|-|
|[高 （最低的 16 位的高 8 位）](operator-high.md)|[HIGH32 （64 位的高 32 位）](operator-high32.md)|[HIGHWORD （高 16 位的最低的 32 位）](operator-highword.md)|
|[长度 （数组中的元素数）](operator-length.md)|[LENGTHOF （数组中的元素数）](operator-lengthof.md)|[低 （低 8 位）](operator-low.md)|
|[LOW32 （低 32 位）](operator-low32.md)|[LOWWORD （低 16 位）](operator-lowword.md)|[OPATTR （获取参数类型信息）](operator-opattr.md)|
|[PTR （指针类型或到）](operator-ptr.md)|[短 （标记短标签类型）](operator-short.md)|[大小 （类型或变量的大小）](operator-size.md)|
|[SIZEOF （类型或变量的大小）](operator-sizeof.md)|[此 （当前位置）](operator-this.md)|[类型 （get 表达式类型）](operator-type.md)|
|[.类型 （get 参数类型信息）](operator-dot-type.md)|||

## <a name="see-also"></a>请参阅

[Microsoft 宏汇编程序参考](microsoft-macro-assembler-reference.md)<br/>

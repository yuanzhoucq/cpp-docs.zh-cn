---
title: ARM 汇编程序诊断消息
ms.date: 08/30/2018
f1_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
helpviewer_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
ms.openlocfilehash: 72c1ea64501ef8104fee9bdf914a1464c07c3b76
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449222"
---
# <a name="arm-assembler-diagnostic-messages"></a>ARM 汇编程序诊断消息

Microsoft ARM 汇编程序 (*armasm*) 遇到它们时发出诊断警告和错误。 本文描述了最常见的消息。

## <a name="syntax"></a>语法

> <em>文件名</em> **(** <em>行号</em> **):** \[**错误**|**警告**] **A**<em>数</em> **:** *消息*

## <a name="diagnostic-messages---errors"></a>诊断消息的错误

> A2193： 此指令生成不可预知的行为

ARM 体系结构不能保证在执行此指令时，会发生什么情况。  有关此指令的定义完善的窗体的详细信息，请查阅[ARM 体系结构参考手册](https://go.microsoft.com/fwlink/p/?linkid=246464)。

```asm
    ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior
```

> A2196： 不能以 16 位编码指令

指定的指令无法编码为 16 位 Thumb 指令。  指定的 32 位指令，或重新排列代码以最终的目标标签到 16 位指令的范围。

在组装器可能会尝试进行编码的 16 位分支和失败，出现此错误，即使编码的 32 位分支。 通过使用来解决此问题`.W`说明符以显式标记为 32 位分支。

```asm
    ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits

    B.W label             ; OK
    B.N label             ; A2196: instruction cannot be encoded in 16 bits
    SPACE 10000
label
```

> A2202:不允许滚动块区域中预 UAL 指令语法

Thumb 代码必须使用统一组装器语言 (UAL) 语法。  旧语法不再被接受

```asm
    ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region
    ADDSEQ r0, r1         ; OK
```

> A2513:旋转必须为偶数

在 ARM 模式下，没有用于指定常量替代语法。  而不是编写`#<const>`，可以编写`#<byte>,#<rot>`，它表示获取通过旋转值的常量值`<byte>`向右`<rot>`。  当您使用此语法时，必须将的值设置`<rot>`甚至。

```asm
    MOV r0, #4, #2       ; OK
    MOV r0, #4, #1       ; A2513: Rotation must be even
```

> A2557:返回写入的字节数不正确

NEON 结构上加载和存储的说明 (`VLDn`， `VSTn`)，没有用于指定回写到基寄存器替代语法。  而不是将一个感叹号 （！） 置于地址后，可以指定即时值，该值指示要添加到基寄存器的偏移量。  如果您使用此语法，必须指定确切的已加载或存储由指令的字节数。

```asm
    VLD1.8 {d0-d3}, [r0]!         ; OK
    VLD1.8 {d0-d3}, [r0], #32     ; OK
    VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back
```

## <a name="diagnostic-messages---warnings"></a>诊断消息的警告

> A4228:对齐值超出了区域对齐方式;不能保证的对齐方式

中指定的对齐方式`ALIGN`指令大于包含它的对齐方式`AREA`。  因此，在组装器不能保证`ALIGN`指令将起作用。

若要解决此问题，可以指定在`AREA`指令`ALIGN`等于或大于所需的对齐方式的属性。

```asm
AREA |.myarea1|
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed

AREA |.myarea2|,ALIGN=3
ALIGN 8           ; OK
```

> A4508:此旋转的常量的使用不推荐使用

在 ARM 模式下，没有用于指定常量替代语法。  而不是编写`#<const>`，可以编写`#<byte>,#<rot>`，它表示获取通过旋转值的常量值`<byte>`向右`<rot>`。  在某些上下文中，ARM 已弃用这些旋转的常量的使用。 在这些情况下，使用基本`#<const>`语法相反。

```asm
    ANDS r0, r0, #1                ; OK
    ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated
```

> A4509:这种形式的条件指令已弃用

通过 ARM ARMv8 体系结构中已弃用这种形式的条件指令。 我们建议更改代码以使用的条件分支。 若要查看仍受支持的条件说明，请查阅[ARM 体系结构参考手册](https://go.microsoft.com/fwlink/p/?linkid=246464)。

此警告不是时发出 **-oldit**使用命令行开关。

```asm
    ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated
```

## <a name="see-also"></a>请参阅

[ARM 汇编程序命令行参考](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[ARM 汇编程序指令](../../assembler/arm/arm-assembler-directives.md)<br/>

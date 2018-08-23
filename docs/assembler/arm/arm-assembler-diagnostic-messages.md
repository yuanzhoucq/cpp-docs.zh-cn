---
title: ARM 汇编程序诊断消息 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1616b4bd9c4b64e771ec537a1b8cd7b582702222
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052768"
---
# <a name="arm-assembler-diagnostic-messages"></a>ARM 汇编程序诊断消息
Microsoft ARM 汇编程序 (*armasm*) 遇到它们时发出诊断警告和错误。 本指南介绍了最常见的消息。  
  
## <a name="syntax"></a>语法  
  
```  
  
filename(lineno) : [error|warning] Anum: message  
```  
  
## <a name="diagnostic-messages"></a>诊断消息  
  
### <a name="errors"></a>错误  
 A2193： 此指令生成不可预知的行为  
 ARM 体系结构不能保证在执行此指令时，会发生什么情况。  有关此指令的定义完善的窗体的详细信息，请查阅[ARM 体系结构参考手册](http://go.microsoft.com/fwlink/p/?linkid=246464)。  
  
```  
  
ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior  
  
```  
  
 A2196： 不能在 16 位编码指令  
 将指定的指令不能为 16 位 Thumb 指令进行编码。  指定的 32 位指令，或重新排列代码以使目标标签的 16 位指令的范围。  
  
 汇编程序可能会尝试进行编码的 16 位分支和失败，出现此错误，即使 32 位分支是编码。 你可以通过结合使用来解决此问题`.W`说明符来显式标记为 32 位分支。  
  
```  
  
  ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits  
  
  B.W label             ; OK  
  B.N label             ; A2196: instruction cannot be encoded in 16 bits  
  SPACE 10000  
label  
  
```  
  
 不允许在 THUMB 区域 A2202: Pre UAL 指令语法  
 Thumb 代码必须使用统一汇编程序语言 (UAL) 语法。  不再接受旧语法  
  
```  
  
ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region  
ADDSEQ r0, r1         ; OK  
  
```  
  
 A2513： 旋转必须为偶数  
 在 ARM 模式下，没有用于指定常量备用语法。  而不是编写`#<const>`，你可以编写`#<byte>,#<rot>`，它表示获取通过旋转值的常量值`<byte>`向右`<rot>`。  当你使用此语法时，必须使值`<rot>`甚至。  
  
```  
  
MOV r0, #4, #2       ; OK  
MOV r0, #4, #1       ; A2513: Rotation must be even  
  
```  
  
 返回写入的字节的数目不正确 A2557:  
 对霓虹灯结构加载和存储指令 (`VLDn`， `VSTn`)，没有用于指定回写到基寄存器备用语法。  不要在感叹号 （！） 地址后，你可以指定即时值，该值指示要添加到基寄存器的偏移量。  如果你使用此语法，你必须指定确切的已加载或存储的指令的字节数。  
  
```  
  
VLD1.8 {d0-d3}, [r0]!         ; OK  
VLD1.8 {d0-d3}, [r0], #32     ; OK  
VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back  
  
```  
  
### <a name="warnings"></a>警告  
 A4228： 对齐值超过区域对齐;不能保证的对齐方式  
 中指定的对齐方式`ALIGN`指令大于封闭的对齐方式`AREA`。  因此，汇编程序也不能保证`ALIGN`指令将起作用。  
  
 若要解决此问题，可以指定在`AREA`指令`ALIGN`等于或大于的所需的对齐方式的属性。  
  
```  
  
AREA |.myarea1|  
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed  
  
AREA |.myarea2|,ALIGN=3  
ALIGN 8           ; OK  
  
```  
  
 A4508： 不建议使用此 rotated 常量  
 在 ARM 模式下，没有用于指定常量备用语法。  而不是编写`#<const>`，你可以编写`#<byte>,#<rot>`，它表示获取通过旋转值的常量值`<byte>`向右`<rot>`。  在某些上下文中，ARM 已否决这些 rotated 常量中的使用。 在这些情况下，使用 basic`#<const>`语法相反。  
  
```  
  
ANDS r0, r0, #1                ; OK  
ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated  
  
```  
  
 这种形式的条件指令已弃用 A4509:  
 这种形式的条件指令已否决 ARMv8 体系结构中的 ARM。 我们建议你更改代码以使用条件分支。 若要查看哪些条件指令仍受支持，请查阅[ARM 体系结构参考手册](http://go.microsoft.com/fwlink/p/?linkid=246464)。  
  
 此警告不时发出`-oldit`使用命令行开关。  
  
```  
  
ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated  
  
```  
  
## <a name="see-also"></a>请参阅  
 [ARM 汇编程序命令行参考](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [ARM 汇编程序指令](../../assembler/arm/arm-assembler-directives.md)
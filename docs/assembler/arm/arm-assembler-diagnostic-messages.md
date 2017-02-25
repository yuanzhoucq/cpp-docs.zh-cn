---
title: "ARM Assembler Diagnostic Messages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ARM Assembler Diagnostic Messages
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft 臂组装器 \(*armasm*） 时遇到这些系统发出诊断的警告和错误。  本文介绍的最常遇到的消息。  
  
## 语法  
  
```  
  
filename(lineno) : [error|warning] Anum: message  
```  
  
## 诊断消息  
  
### 错误  
 A2193: 此指令将产生不可预知的行为  
 ARM 体系结构不能保证在执行此指令时，会发生什么情况。  有关此指令的明确定义窗体的详细信息，请参阅[臂体系结构参考手册 》](http://go.microsoft.com/fwlink/?LinkId=246464)。  
  
```  
  
ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior  
  
```  
  
 A2196: 无法在 16 位编码指令  
 指定的指令不能编码为一个 16 位拇指指令中。  指定 32 位的说明，或重新排列带入 16 位指令的范围的目标标签代码。  
  
 汇编程序可能试图编码在 16 位分支和失败，出现此错误，即使一个 32 位分支是 encodable。  您可以解决此问题，通过使用`.W`说明符显式标记为 32 位的分支。  
  
```  
  
  ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits  
  
  B.W label             ; OK  
  B.N label             ; A2196: instruction cannot be encoded in 16 bits  
  SPACE 10000  
label  
  
```  
  
 A2202: 前的双重指令语法不允许滚动块区域中  
 滚动块的代码必须使用统一 $ 汇编程序 l 语言 （双重\) 的语法。  不再接受旧语法  
  
```  
  
ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region  
ADDSEQ r0, r1         ; OK  
  
```  
  
 A2513： 旋转必须为偶数  
 在 ARM 模式下，没有指定常数的替代语法。  代替编写`#<const>`，您可以编写`#<byte>,#<rot>`，它代表所得到的旋转值的常量值`<byte>`权限， `<rot>`。  当您使用此语法时，您必须进行的值`<rot>`甚至。  
  
```  
  
MOV r0, #4, #2       ; OK  
MOV r0, #4, #1       ; A2513: Rotation must be even  
  
```  
  
 A2557： 要重新写入的字节数不正确  
 霓虹灯光结构上加载和存储指令 \(`VLDn`， `VSTn`），没有指定基寄存器的写回的替代语法。  而不是放置一个感叹号 \(\!\) 地址后，您可以指定即时值，指示要添加到基寄存器的偏移量。  如果您使用此语法，则必须指定确切的已加载或存储指令的字节数。  
  
```  
  
VLD1.8 {d0-d3}, [r0]!         ; OK  
VLD1.8 {d0-d3}, [r0], #32     ; OK  
VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back  
  
```  
  
### 警告  
 A4228: 对齐值超出了区域对齐。 不能保证的对齐方式  
 在中指定的对齐方式`ALIGN`指令的对齐方式的封闭大于`AREA`。  因此，汇编程序不能保证的`ALIGN`指令将得到遵守。  
  
 要解决此问题，您可以指定在`AREA`指令`ALIGN`等于或大于所需的对齐属性。  
  
```  
  
AREA |.myarea1|  
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed  
  
AREA |.myarea2|,ALIGN=3  
ALIGN 8           ; OK  
  
```  
  
 A4508： 建议使用此旋转常数的使用  
 在 ARM 模式下，没有指定常数的替代语法。  代替编写`#<const>`，您可以编写`#<byte>,#<rot>`，它代表所得到的旋转值的常量值`<byte>`权限， `<rot>`。  在某些情况下，ARM 已否决这些旋转常数的使用。  在这些情况下，使用基本`#<const>`语法相反。  
  
```  
  
ANDS r0, r0, #1                ; OK  
ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated  
  
```  
  
 A4509： 建议使用这种形式的条件指令  
 这种形式的条件指令已被否决的 ARM ARMv8 体系结构中。  我们建议您更改代码以使用条件分支。  若要查看哪些条件指令仍受支持，请参阅[臂体系结构参考手册 》](http://go.microsoft.com/fwlink/?LinkId=246464)。  
  
 此警告不是何时发出 `-oldit` 使用命令行开关。  
  
```  
  
ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated  
  
```  
  
## 请参阅  
 [ARM Assembler Command\-Line Reference](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [ARM Assembler Directives](../../assembler/arm/arm-assembler-directives.md)
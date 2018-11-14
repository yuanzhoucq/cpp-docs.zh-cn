---
title: MASM 宏
ms.date: 11/04/2016
ms.assetid: 21410432-72fc-4795-bc93-e78123f9f14f
ms.openlocfilehash: 8a00852a3a763aae5fda34d7e0fde664997a0bdb
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328820"
---
# <a name="masm-macros"></a>MASM 宏

为了简化使用[原始伪操作](../build/raw-pseudo-operations.md)，有一组在 ksamd64.inc，可以用于创建典型的过程序言和尾声中定义的宏。

## <a name="remarks"></a>备注

|宏|描述|
|-----------|-----------------|
|alloc_stack(n)|分配 （使用子 rsp，n） n 个字节的堆栈帧并发出相应的展开信息 (.allocstack n)|
|save_reg reg 本地化|将非易失寄存器 reg 保存在 RSP 偏移量位置处的堆栈上，并发出相应的展开信息。 (.savereg reg，loc)|
|push_reg reg|将非易失寄存器 reg 推送到堆栈上，并发出相应的展开信息。 (.pushreg reg)|
|rex_push_reg reg|将非易失寄存器保存使用 2 字节推送到堆栈，并发出相应展开函数中的第一个指令，以确保函数是可热修补推送是否应使用此信息 (.pushreg reg)。|
|save_xmm128 reg 本地化|将非易失 XMM 寄存器保存在 RSP 偏移量位置处的堆栈上的注册表，并发出相应的展开 （.savexmm128 reg，loc） 的信息|
|set_frame reg、 偏移量|设置框架注册 reg 是 RSP + 偏移量 （使用 mov 或逆转），并发出相应的展开 （.set_frame reg，偏移量） 的信息|
|push_eflags|推送与 pushfq 指令 eflags 并发出相应的展开信息 (.alloc_stack 8)|

下面是示例函数 prolog 使用宏的正确用法：

```asm
SkFrame struct
Fill    dq ?; fill to 8 mod 16
SavedRdi dq ?; saved register RDI
SavedRsi dq ?; saved register RSI
SkFrame ends

sampleFrame struct
Filldq?; fill to 8 mod 16
SavedRdidq?; Saved Register RDI
SavedRsi  dq?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
alloc_stack(sizeof sampleFrame)
save_reg rdi, sampleFrame.SavedRdi
save_reg rsi, sampleFrame.SavedRsi
.end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here’s the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="see-also"></a>请参阅

[MASM 的展开帮助器](../build/unwind-helpers-for-masm.md)
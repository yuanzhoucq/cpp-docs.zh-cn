---
title: MASM 宏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 21410432-72fc-4795-bc93-e78123f9f14f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 403220306a2585b1506a990664eaa2ec8f2ac1a3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368689"
---
# <a name="masm-macros"></a>MASM 宏
为了简化使用的[原始伪操作](../build/raw-pseudo-operations.md)，有一套 ksamd64.inc，可以用于创建典型过程序言和尾声中定义的宏。  
  
## <a name="remarks"></a>备注  
  
|宏|描述|  
|-----------|-----------------|  
|alloc_stack(n)|分配 （使用子 rsp，n） 的 n 个字节的堆栈帧并发出相应的展开信息 (.allocstack n)|  
|save_reg reg 本地化|保存在位于 RSP 偏移量 loc 的堆栈上的非易失寄存器 reg 并发出相应的展开信息。 (.savereg reg，loc)|  
|push_reg reg|将非易失寄存器 reg 推送到堆栈上，并发出相应的展开信息。 (.pushreg reg)|  
|rex_push_reg reg|使用 2 字节推送到堆栈上保存非易失寄存器并发出相应的展开函数中的第一个指令，以确保函数是热修补推送是否应使用此信息 (.pushreg reg)。|  
|save_xmm128 reg 本地化|将非易失 XMM 寄存器保存 RSP 偏移量的位置，在堆栈上的注册表并发出相应的展开信息 （.savexmm128 reg、 loc）|  
|set_frame reg、 偏移量|设置帧寄存器 reg，若要将 RSP + 偏移量 （使用 mov、 或逆转），并发出相应的展开信息 （.set_frame reg、 偏移量）|  
|push_eflags|推送与 pushfq 指令 eflags 并发出相应的展开信息 (.alloc_stack 8)|  
  
 下面是示例函数 prolog 与宏的正确用法：  
  
```  
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
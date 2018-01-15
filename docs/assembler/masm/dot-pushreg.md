---
title: ".PUSHREG |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .PUSHREG
dev_langs: C++
helpviewer_keywords: .PUSHREG directive
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f85e1082c38eb2880ff6ad3c15b4842ebf015ca6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="pushreg"></a>.PUSHREG
生成`UWOP_PUSH_NONVOL`指定注册号码，使用的当前偏移量在序言展开代码入口。  
  
## <a name="syntax"></a>语法  
  
```  
.PUSHREG register  
```  
  
## <a name="remarks"></a>备注  
 .PUSHREG 允许 ml64.exe 用户指定如何帧函数展开，并只允许在序言从内[PROC](../../assembler/masm/proc.md)帧声明移到[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。 这些指令不会生成代码;它们仅生成`.xdata`和`.pdata`。 .PUSHREG 前面应带有实际实现的操作要展开的说明。 它是一个包装展开指令和它们专用于在宏中展开以确保协议的代码的好办法。  
  
 有关详细信息，请参阅[x64 (ml64.exe) 的 MASM](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## <a name="sample"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例演示如何将非易失性 tegisters 推送。  
  
### <a name="code"></a>代码  
  
```  
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE  
_text SEGMENT  
Example1 PROC FRAME  
   push r10  
.pushreg r10  
   push r15  
.pushreg r15  
   push rbx  
.pushreg rbx  
   push rsi  
.pushreg rsi  
.endprolog  
   ; rest of function ...  
   ret  
Example1 ENDP  
_text ENDS  
END  
```  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)
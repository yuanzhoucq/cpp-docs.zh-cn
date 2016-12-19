---
title: ".SAVEXMM128 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ".SAVEXMM128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".SAVEXMM128 directive"
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .SAVEXMM128
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成或 `UWOP_SAVE_XMM128` 使用当前 \(偏移量，或 `UWOP_SAVE_XMM128_FAR` 展开指定的 XMM 寄存器的代码项和扭曲。  MASM 将选择最有效的编码。  
  
## 语法  
  
```  
.savexmm128 xmmreg , offset  
```  
  
## 备注  
 .SAVEXMM128 允许 ml64.exe 用户指定框架功能如何展开和在序言中只允许，从 [PROC](../../assembler/masm/proc.md) 帧声明扩展到 [.ENDPROLOG](../../assembler/masm/dot-endprolog.md) 指令。  这些指令不生成代码;它们只生成 `.xdata` 和 `.pdata`。  .SAVEXMM128 应在实际实现将展开的事件的命令之后。  最好包装展开指令及其在宏被视为展开确保协议的代码。  
  
 `offset` 必须是多个为 16。  
  
 有关更多信息，请参见 [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)
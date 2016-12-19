---
title: ".SAVEREG | Microsoft Docs"
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
  - ".SAVEREG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".SAVEREG directive"
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .SAVEREG
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成或 `UWOP_SAVE_NONVOL` 或 `UWOP_SAVE_NONVOL_FAR` 展开指定的寄存器 \(`reg`\) 和扭曲 \(`offset`\) 代码项使用当前 \(偏移量，。  MASM 将选择最有效的编码。  
  
## 语法  
  
```  
.SAVEREG reg, offset  
```  
  
## 备注  
 .SAVEREG 允许 ml64.exe 用户指定框架功能如何在序言中展开并且只允许，从 [PROC](../../assembler/masm/proc.md) 帧声明扩展到 [.ENDPROLOG](../../assembler/masm/dot-endprolog.md) 指令。  这些指令不生成代码;它们只生成 `.xdata` 和 `.pdata`。  .SAVEREG 应在实际实现将展开的事件的命令之后。  最好包装展开指令及其在宏被视为展开确保协议的代码。  
  
 有关更多信息，请参见 [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)
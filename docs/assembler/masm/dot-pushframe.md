---
title: ".PUSHFRAME | Microsoft Docs"
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
  - ".PUSHFRAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".PUSHFRAME directive"
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .PUSHFRAME
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成 `UWOP_PUSH_MACHFRAME` 展开的代码项。  如果选项 `code` 指定，则展开的代码项修饰符 1。  否则该修饰符为 0。  
  
## 语法  
  
```  
.PUSHFRAME [code]  
```  
  
## 备注  
 .PUSHFRAME 允许 ml64.exe 用户指定框架功能如何在序言中展开并且只允许，从 [PROC](../../assembler/masm/proc.md) 帧声明扩展到 [.ENDPROLOG](../../assembler/masm/dot-endprolog.md) 指令。  这些指令不生成代码;它们只生成 `.xdata` 和 `.pdata`。  .PUSHFRAME 应在实际实现将展开的事件的命令之后。  最好包装展开指令及其在宏被视为展开确保协议的代码。  
  
 有关更多信息，请参见 [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)
---
title: ".FPO | Microsoft Docs"
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
  - ".FPO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".FPO directive"
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .FPO
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

.FPO 指令控件发出调试记录到 .debug$F 段或部分。  
  
## 语法  
  
```  
  
FPO (  
cdwLocals  
,   
cdwParams  
,   
cbProlog  
,   
cbRegs  
,   
fUseBP  
,   
cbFrame  
)  
  
```  
  
#### 参数  
 `cdwLocals`  
 局部变量的数字，无符号 32 位值。  
  
 `cdwParams`  
 参数，无符号 16 位值的范围在 DWORDS 的。  
  
 *cbProlog*  
 中的字节数 prolog 代码，无符号 8 位的值。  
  
 `cbRegs`  
 保存的数字注册。  
  
 `fUseBP`  
 指示是否已分配的 EBP 寄存器。  0 或 1。  
  
 *cbFrame*  
 指示框架类型。  有关更多信息，请参见[FPO\_DATA](http://msdn.microsoft.com/library/windows/desktop/ms679352)。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)
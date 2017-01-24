---
title: "C 运行时错误 R6030 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6030"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6030"
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
caps.latest.revision: 9
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C 运行时错误 R6030
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CRT 未初始化  
  
 如果要使用 CRT，但是未执行 CRT 启动代码，则会发生此错误。  如果链接器开关 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 用于重写默认启动地址（通常为 **mainCRTStartup**、用于控制台 EXE 的 **wmainCRTStartup**、用于 Windows EXE 的 **WinMainCRTStartup** 或 **wWinMainCRTStartup** 或者是用于 DLL 的 **\_DllMainCRTStartup**），则可能发生此错误。  除非在启动时调用上述函数之一，否则将不初始化 C 运行时。
---
title: "链接器工具警告 LNK4237 | Microsoft Docs"
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
  - "LNK4237"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4237"
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4237
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在从“dll”导入时指定了 \/SUBSYSTEM:NATIVE；请使用 \/SUBSYSTEM:CONSOLE 或 \/SUBSYSTEM:WINDOWS。  
  
 在生成直接使用一个或多个下列 DLL 的 Windows \(Win32\) 应用程序时指定了 [\/SUBSYSTEM:NATIVE](../../build/reference/subsystem-specify-subsystem.md)：  
  
-   kernel32.dll  
  
-   gdi32.dll  
  
-   user32.dll  
  
-   msvcrt\* dll 之一。  
  
 通过不指定 **\/SUBSYSTEM:NATIVE** 来解决此警告。
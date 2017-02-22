---
title: "其他 LIB 输出 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Lib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "输出文件, LIB"
ms.assetid: 656864a6-0b7a-4633-8dc6-ee3b1766d836
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 其他 LIB 输出
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在默认模式下，可以使用 \/LIST 选项显示有关结果库的信息。  可将此输出重定向到文件。  
  
 LIB 显示版权和版本信息并回显命令文件（除非使用了 \/NOLOGO 选项）。  
  
 当键入 `lib` 但没有其他输入时，LIB 显示一条汇总其选项的用法语句。  
  
 LIB 发出的错误和警告消息具有 LNK*nnnn* 格式。  LINK、DUMPBIN 和 EDITBIN 工具也使用此错误范围。  可以通过在“输出”窗口中选择错误并按 F1 键可得到帮助。  
  
## 请参阅  
 [LIB 概述](../../build/reference/overview-of-lib.md)
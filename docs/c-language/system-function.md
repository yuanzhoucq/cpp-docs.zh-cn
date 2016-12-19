---
title: "系统函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "系统函数"
ms.assetid: 0786ccdc-20cd-4d96-b3d8-3230507c3066
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 系统函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.10.4.5 system** 函数执行字符串的内容和模式  
  
 **system** 函数执行内部操作系统命令，或者 C 程序中（而不是命令行中）的 .EXE、.COM（Windows NT 中的 .CMD）或 .BAT 文件。  
  
 系统函数查找命令解释器，它通常是 Windows NT 操作系统中的 CMD.EXE 或 Windows 中的 COMMAND.COM。  系统函数随后将参数字符串传递到命令解释器。  
  
 有关详细信息，请参阅[system、\_wsystem](../c-runtime-library/reference/system-wsystem.md)。  
  
## 请参阅  
 [库函数](../c-language/library-functions.md)
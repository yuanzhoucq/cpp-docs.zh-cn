---
title: "NMAKE 错误 U1056 | Microsoft Docs"
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
  - "U1056"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1056"
ms.assetid: da855728-b69e-413c-83ed-df912126215e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 错误 U1056
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法找到命令处理器  
  
 命令处理器未在 **COMSPEC** 或 **PATH** 环境变量指定的路径中。  
  
 当执行命令时，NMAKE 将 COMMAND.COM 或 CMD.EXE 用作命令处理器。  它首先在 **COMSPEC** 中设置的路径中查找命令处理器。  如果 **COMSPEC** 不存在，则 NMAKE 搜索 **PATH** 中指定的目录。
---
title: "链接器工具错误 LNK1223 | Microsoft Docs"
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
  - "LNK1223"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1223"
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1223
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无效或损坏的文件：文件包含无效的 .pdata 基值  
  
 对于使用 pdata 的 RISC 平台，如果编译器发出具有无序条目的 .pdata 部分，则将发生此错误。  
  
 若要解决此问题，请尝试编译但不启用 [\/GL \(Whole Program Optimization\)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md)。  在某些情况下，空的函数体也可能导致此错误。
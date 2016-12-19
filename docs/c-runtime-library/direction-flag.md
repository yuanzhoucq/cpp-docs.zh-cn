---
title: "方向标志 | Microsoft Docs"
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
  - "c.flags"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "方向标志"
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 方向标志
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

方向标志是CPU标识指向Intel的80x86处理器。  它适用于所有使用REP（重复）前缀的所有程序集指令，如 MOVS、MOVSD，MOVSW 和其他。  如果方向标识清除，地址提供的可用的说明会增加。  
  
 C 运行期程序假定方向标志清除。  如果使用 C 运行时函数的其他函数，您必须确保其他函数不理会方向标志或还原其为原始条件。  在输入时期望方向标志清除能使运行时代码更加快速、更高效。  
  
 C 运行库函数，例如字符串处理和缓冲区处理例程，希望方向标志被清除。  
  
## 请参阅  
 [CRT 库功能](../c-runtime-library/crt-library-features.md)
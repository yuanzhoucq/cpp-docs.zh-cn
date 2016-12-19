---
title: "链接器工具警告 LNK4010 | Microsoft Docs"
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
  - "LNK4010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4010"
ms.assetid: 2824cf99-4174-4b60-a6e2-c01e9f1ee52d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无效的子系统版本号 number；假定为默认子系统版本  
  
 您可以指定映像的子系统 \([\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)\) 的版本。  每个子系统都有最低版本要求。  如果指定的版本低于最低要求，将发生此警告，并且该链接器将仅使用默认子系统。
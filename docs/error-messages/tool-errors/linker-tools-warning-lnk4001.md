---
title: "链接器工具警告 LNK4001 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4001"
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 链接器工具警告 LNK4001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未指定对象文件；已使用库  
  
 传递给链接器一个或多个 .lib 文件，但没有 .obj 文件。  
  
 由于链接器不能访问 .lib 文件中的信息（它能够访问 .obj 文件中的此信息），因此，此警告指示您将必须显式地指定其他链接器选项。  例如，您可能必须指定 [\/MACHINE](../../build/reference/machine-specify-target-platform.md)、[\/OUT](../../build/reference/out-output-file-name.md) 或 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 选项。
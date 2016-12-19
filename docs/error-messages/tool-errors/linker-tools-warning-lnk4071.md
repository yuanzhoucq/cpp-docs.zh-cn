---
title: "链接器工具警告 LNK4071 | Microsoft Docs"
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
  - "LNK4071"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4071"
ms.assetid: 803f8c34-8219-4f55-a4ae-7133ceff2ba3
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4071
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法增量链接到后面的链接上  
  
 LINK 找到了一个或多个符号的多个定义，尽管有错误，但还是使用了 [\/FORCE](../../build/reference/force-force-file-output.md) 或 **\/FORCE:MULTIPLE** 创建输出文件。  LINK 删除了增量状态 \(.ilk\) 文件。
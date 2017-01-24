---
title: "生成文件中的长文件名 | Microsoft Docs"
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
helpviewer_keywords: 
  - "长文件名"
  - "NMAKE 程序, 长文件名"
ms.assetid: 626d56fc-8879-46ba-9c2d-dd386c78cccc
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 生成文件中的长文件名
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将长文件名用双引号引起来，如下所示：  
  
```  
all : "VeryLongFileName.exe"  
```  
  
## 请参阅  
 [生成文件的内容](../build/contents-of-a-makefile.md)
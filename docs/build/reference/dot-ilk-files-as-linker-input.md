---
title: "用作链接器输入的 .Ilk 文件 | Microsoft Docs"
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
  - ".ilk 文件"
  - "ILK 文件"
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 用作链接器输入的 .Ilk 文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在增量链接时，LINK 更新在第一次增量链接期间创建的 .ilk 状态文件。  该文件和 .exe 文件或 .dll 文件具有相同的基名称，并具有扩展名 .ilk。  在后面的增量链接期间，LINK 更新 .ilk 文件。  如果缺少 .ilk 文件，则 LINK 执行完全链接并创建新的 .ilk 文件。  如果 .ilk 文件无法使用，则 LINK 执行非增量链接。  有关增量链接的详细信息，请参见[渐进式链接 \(\/INCREMENTAL\)](../../build/reference/incremental-link-incrementally.md) 选项。  
  
## 请参阅  
 [LINK 输入文件](../../build/reference/link-input-files.md)   
 [链接器选项](../../build/reference/linker-options.md)
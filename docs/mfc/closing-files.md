---
title: "关闭文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "文件 [C++], 关闭"
  - "MFC [C++], 文件操作"
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 关闭文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

像往常一样在 I\/O 操作，完成了文件，必须关闭它。  
  
#### 关闭单个文件  
  
1.  使用 **关闭** 成员函数。  如果需要此函数，关闭文件系统上文件并刷新缓冲区。  
  
 如果分配上的 [CFile](../mfc/reference/cfile-class.md) \(如帧对象在 [打开文件](../mfc/opening-files.md)显示的示例中\)，则对象将自动关闭并销毁在超出范围。  注意删除 `CFile` 对象，不会在文件系统中的物理文件。  
  
## 请参阅  
 [文件](../mfc/files-in-mfc.md)
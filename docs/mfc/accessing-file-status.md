---
title: "访问文件状态 | Microsoft Docs"
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
  - "示例 [MFC], 文件状态"
  - "文件状态 [C++]"
  - "文件 [C++], 访问"
  - "文件 [C++], 状态信息"
  - "文件的状态"
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 访问文件状态
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CFile` 还支持获取文件状态，包括文件是否存在，创建和修改日期和时间、逻辑大小和路径。  
  
### 若要获取状态文件  
  
1.  使用 [CFile](../mfc/reference/cfile-class.md) 类获取和设置的文件信息。  一个有用的应用程序是使用 `CFile` 静态成员函数 **GetStatus** 来确定文件是否存在。  如果指定的文件不存在，则**GetStatus**返回0。  
  
 因此，您是否能使用 **GetStatus** 的结果确定使用 **CFile::modeCreate** 标志，在打开文件，如下面的示例所示：  
  
 [!code-cpp[NVC_MFCFiles#3](../mfc/codesnippet/CPP/accessing-file-status_1.cpp)]  
  
 有关相关信息，请参阅[Serialization](../mfc/serialization-in-mfc.md)。  
  
## 请参阅  
 [文件](../mfc/files-in-mfc.md)
---
title: "读取和写入文件 | Microsoft Docs"
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
  - "CFile 类, 对象"
  - "CFile 类, 读取和写入 CFile 对象"
  - "示例 [MFC], 读取文件"
  - "示例 [MFC], 写入文件"
  - "文件 [C++], 读取"
  - "文件 [C++], 写入"
  - "MFC [C++], 文件操作"
  - "读取文件"
  - "写入文件 [C++]"
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 读取和写入文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果使用的 C 运行库文件处理的函数，读取和写入操作的 MFC 看起来很熟悉。  本文描述用于读取直接从和直接写入 `CFile` 对象。  还可以使用 [CArchive](../mfc/reference/carchive-class.md) 类执行的缓存文件 I\/O。  
  
#### 读取和写入文件  
  
1.  使用 **读取** 和 **写入** 成员函数读取和写入文件中的数据。  
  
     \- 或 \-  
  
2.  `Seek` 成员函数为移动还为该文件内的偏移量。  
  
 **读取** 采用指向缓冲区读取的字节数和并返回实际读取的字节数。  如果所需的字节数无法读取，因为文件尾 \(EOF\) 到达实际读取的字节数，返回。  如果读取任何错误，将引发异常。  **写入** 类似于 **读取**，编写的字节数，但未返回。  如果写入错误，包含不写入指定的所有字节为止，将引发异常。  如果您拥有有效的 `CFile` 对象，如下面的示例所示，您可以从中读取或写入。它：  
  
 [!code-cpp[NVC_MFCFiles#2](../mfc/codesnippet/CPP/reading-and-writing-files_1.cpp)]  
  
> [!NOTE]
>  您通常应执行在 **try**\/**catch** 异常处理块中的输入\/输出操作。  有关更多信息，请参见 [异常处理 \(MFC\)](../mfc/exception-handling-in-mfc.md)。  
  
## 请参阅  
 [文件](../mfc/files-in-mfc.md)
---
title: "文件 I/O 类 | Microsoft Docs"
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
  - "vc.classes.file"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "磁盘文件类"
  - "文件 I/O 类 [C++]"
  - "I/O [C++], MFC 类"
  - "I/O [MFC], 类"
  - "内存文件类"
  - "OLE 流"
  - "套接字类"
  - "stdio 类"
  - "stream 类"
  - "已转换的 stream 类"
ms.assetid: 92821c3f-d9e1-47f6-98c9-3b632d86e811
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文件 I/O 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些类提供一个接口以传统磁盘文件、文件、内存流活动和 Windows 套接字。  从 `CFile` 派生的所有类可用于以 `CArchive` 对象执行序列化。  
  
 使用以下，类特定`CArchive` 和 `CFile`，因此，如果您编写自己输入\/输出处理。  通常不需要从这些类派生。  如果使用应用程序框架，**打开** 和 **保存** 命令的默认实现。**文件** 菜单中处理文件 I\/O \(使用 `CArchive`类\)，因此，只要，重写文档的 `Serialize` 函数提供有关文档的方式的详细信息序列化其内容。  有关类文件并序列化的更多信息，请参见 [MFC 中的文件](../mfc/files-in-mfc.md) 文章和文章 [序列化](../mfc/serialization-in-mfc.md)。  
  
 [CFile](../mfc/reference/cfile-class.md)  
 提供一个接口以二进制文件磁盘文件。  
  
 [CStdioFile](../mfc/reference/cstdiofile-class.md)  
 提供 `CFile` 接口。缓存的磁盘文件流，通常在文本模式。  
  
 [CMemFile](../mfc/reference/cmemfile-class.md)  
 提供 `CFile` 接口。内存文件。  
  
 [CSharedFile](../mfc/reference/csharedfile-class.md)  
 提供 `CFile` 接口共享内存文件。  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 使用 COM `IStream` 接口提供对复合文件 `CFile` 的访问。  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)  
 提供一个 `CFile` 接口给 Windows 套接字。  
  
## 相关类  
 [CArchive](../mfc/reference/carchive-class.md)  
 与`CFile`对象协作通过序列化实现对象的持久性存储 \(请参见[CObject::Serialize](../Topic/CObject::Serialize.md)\)。  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 存档异常。  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 面向文件的异常。  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 用于打开或保存文件提供标准对话框。  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 保留最近使用的文件列表\(MRU\)。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)
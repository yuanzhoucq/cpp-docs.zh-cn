---
title: 文件我-O 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.file
dev_langs:
- C++
helpviewer_keywords:
- disk file classes [MFC]
- stdio classes [MFC]
- OLE streams [MFC]
- I/O [MFC], MFC classes
- translated stream classes [MFC]
- file I/O classes [MFC]
- I/O [MFC], classes
- sockets classes [MFC]
- stream classes [MFC]
- memory file classes [MFC]
ms.assetid: 92821c3f-d9e1-47f6-98c9-3b632d86e811
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b11996aadd58b456aa919d4ff888c783b4ba486e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356181"
---
# <a name="file-io-classes"></a>文件 I/O 类
这些类提供传统的磁盘文件、 内存中文件、 活动流和 Windows 套接字的接口。 所有类派生自`CFile`可以与使用`CArchive`要执行序列化对象。  
  
 使用以下类，尤其是`CArchive`和`CFile`，如果你编写自己的输入/输出处理。 通常不需要派生自这些类。 如果你使用应用程序框架的默认实现**打开**和**保存**上的命令**文件**菜单将处理文件 I/O (使用类`CArchive`)，只要您重写文档的`Serialize`函数提供有关文档序列其内容的方式的详细信息。 有关文件类和序列化的详细信息，请参阅文章[MFC 中的文件](../mfc/files-in-mfc.md)和文章[序列化](../mfc/serialization-in-mfc.md)。  
  
 [CFile](../mfc/reference/cfile-class.md)  
 提供文件接口到二进制磁盘文件。  
  
 [CStdioFile](../mfc/reference/cstdiofile-class.md)  
 提供`CFile`到缓冲的流磁盘文件，通常在文本模式下的接口。  
  
 [CMemFile](../mfc/reference/cmemfile-class.md)  
 提供`CFile`到内存中文件的接口。  
  
 [CSharedFile](../mfc/reference/csharedfile-class.md)  
 提供`CFile`对共享的内存中文件的接口。  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 使用 COM `IStream` 接口为 `CFile` 提供对复合文件的访问权限。  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)  
 为 Windows 套接字提供 `CFile` 接口。  
  
## <a name="related-classes"></a>相关的类  
 [CArchive](../mfc/reference/carchive-class.md)  
 配合`CFile`对象来实现通过序列化的对象的持久存储 (请参阅[cobject:: Serialize](../mfc/reference/cobject-class.md#serialize))。  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 存档异常。  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 面向文件的异常。  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 提供的标准对话框打开或保存文件。  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 维护最近使用的 (MRU) 文件列表。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)


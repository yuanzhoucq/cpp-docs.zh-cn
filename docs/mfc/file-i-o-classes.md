---
title: 文件 I/o 类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.file
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
ms.openlocfilehash: 914325ec56f0cae30c7293305496d65f358f2731
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405802"
---
# <a name="file-io-classes"></a>文件 I/O 类

这些类提供传统的磁盘文件、 内存中的文件、 活动流和 Windows 套接字的接口。 所有的类派生自`CFile`可与`CArchive`对象执行序列化。

使用以下类，特别`CArchive`和`CFile`，如果写入输入/输出处理。 通常情况下不需要派生自这些类。 如果使用的应用程序框架的默认实现**开放**并**保存**上的命令**文件**菜单将处理文件 I/O (使用类`CArchive`)，只要您替代文档的`Serialize`函数提供有关如何文档序列化其内容的详细信息。 有关文件类和序列化的详细信息，请参阅文章[MFC 中的文件](../mfc/files-in-mfc.md)与项目[序列化](../mfc/serialization-in-mfc.md)。

[CFile](../mfc/reference/cfile-class.md)<br/>
提供到二进制磁盘文件的文件接口。

[CStdioFile](../mfc/reference/cstdiofile-class.md)<br/>
提供了`CFile`到缓冲的流磁盘文件，通常在文本模式下的接口。

[CMemFile](../mfc/reference/cmemfile-class.md)<br/>
提供了`CFile`到内存中文件的接口。

[CSharedFile](../mfc/reference/csharedfile-class.md)<br/>
提供了`CFile`对共享内存中文件的接口。

[COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
使用 COM `IStream` 接口为 `CFile` 提供对复合文件的访问权限。

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
为 Windows 套接字提供 `CFile` 接口。

## <a name="related-classes"></a>相关的类

[CArchive](../mfc/reference/carchive-class.md)<br/>
所以会与协作`CFile`对象以实施通过序列化对象的持久性存储区 (请参阅[cobject:: Serialize](../mfc/reference/cobject-class.md#serialize))。

[CArchiveException](../mfc/reference/carchiveexception-class.md)<br/>
存档异常。

[CFileException](../mfc/reference/cfileexception-class.md)<br/>
面向文件的异常。

[CFileDialog](../mfc/reference/cfiledialog-class.md)<br/>
打开或保存文件中提供的标准对话框。

[CRecentFileList](../mfc/reference/crecentfilelist-class.md)<br/>
维护最近使用的 (MRU) 文件列表。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)

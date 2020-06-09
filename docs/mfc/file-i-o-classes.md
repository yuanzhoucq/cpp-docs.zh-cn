---
title: 文件 i/o 类
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
ms.openlocfilehash: 2fcf4dfc1388df0df2bc25928ec8541486c6bb2d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615671"
---
# <a name="file-io-classes"></a>文件 I/O 类

这些类为传统磁盘文件、内存中文件、活动流和 Windows 套接字提供接口。 从派生的所有类均 `CFile` 可与对象结合使用 `CArchive` ，以执行序列化。

`CArchive` `CFile` 如果你编写自己的输入/输出处理，则应使用以下类，特别是。 通常不需要从这些类派生。 如果使用应用程序框架， **Open**只要你覆盖**Save** **File** `CArchive` 文档的 `Serialize` 函数以提供有关文档如何序列化其内容的详细信息，"文件" 菜单上的 "打开" 和 "保存" 命令的默认实现将处理文件 i/o （使用类）。 有关文件类和序列化的详细信息，请参阅[MFC 中的文件](files-in-mfc.md)和项目[序列化](serialization-in-mfc.md)。

[CFile](reference/cfile-class.md)<br/>
提供二进制磁盘文件的文件接口。

[CStdioFile](reference/cstdiofile-class.md)<br/>
提供 `CFile` 缓冲流磁盘文件（通常在文本模式下）的接口。

[CMemFile](reference/cmemfile-class.md)<br/>
提供 `CFile` 内存中文件的接口。

[CSharedFile](reference/csharedfile-class.md)<br/>
提供一个 `CFile` 用于内存中共享文件的接口。

[COleStreamFile](reference/colestreamfile-class.md)<br/>
使用 COM `IStream` 接口为 `CFile` 提供对复合文件的访问权限。

[CSocketFile](reference/csocketfile-class.md)<br/>
为 Windows 套接字提供 `CFile` 接口。

## <a name="related-classes"></a>相关类

[CArchive](reference/carchive-class.md)<br/>
使用对象会 `CFile` 通过序列化实现对象的持久存储（请参阅[CObject：：串行化](reference/cobject-class.md#serialize)）。

[CArchiveException](reference/carchiveexception-class.md)<br/>
存档异常。

[CFileException](reference/cfileexception-class.md)<br/>
面向文件的异常。

[CFileDialog](reference/cfiledialog-class.md)<br/>
提供用于打开或保存文件的标准对话框。

[CRecentFileList](reference/crecentfilelist-class.md)<br/>
维护最近使用的（MRU）文件列表。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)

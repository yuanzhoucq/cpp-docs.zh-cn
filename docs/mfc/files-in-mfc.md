---
title: MFC 中的文件
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [MFC], MFC files
- I/O [MFC], MFC classes
- files [MFC], MFC
- files [MFC], serialization
- binary access, binary file operations in MFC
- file I/O classes [MFC]
- I/O [MFC]
- persistence [MFC]
- MFC, file operations
- files [MFC], manipulating
- binary access [MFC]
ms.assetid: ae25e2c5-2859-4679-ab97-438824e93ce1
ms.openlocfilehash: 8b8859e188e42f4419ca7ee7f683cc31de0c75b3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625881"
---
# <a name="files-in-mfc"></a>MFC 中的文件

在 Microsoft 基础类库（MFC）中，类[CFile](reference/cfile-class.md)处理正常文件 i/o 操作。 此系列文章介绍如何打开和关闭文件以及如何读取数据并将数据写入文件。 还讨论了文件状态操作。 有关如何使用 MFC 的基于对象的序列化功能作为在文件中读取和写入数据的另一种方法的说明，请参阅文章[序列化](serialization-in-mfc.md)。

> [!NOTE]
> 使用 MFC 对象时 `CDocument` ，框架会为你执行大量的序列化工作。 具体而言，框架将创建和使用 `CFile` 对象。 只需在替代类的成员函数的重写中编写代码 `Serialize` `CDocument` 。

`CFile` 类为通用二进制文件操作提供了一个接口。 派生自 `CStdioFile` 的 `CMemFile` 和 `CFile` 类以及派生自 `CSharedFile` 的 `CMemFile` 类提供了更专业的文件服务。

有关 MFC 文件处理的替代项的详细信息，请参阅*运行库参考*中的[文件处理](../c-runtime-library/file-handling.md)。

有关派生类的信息 `CFile` ，请参阅[MFC 层次结构图](hierarchy-chart.md)。

## <a name="what-do-you-want-to-do"></a>要执行的操作

*使用 CFile*

- [使用 CFile 打开文件](opening-files.md)

- [使用 CFile 读写文件](reading-and-writing-files.md)

- [使用 CFile 关闭文件](closing-files.md)

- [使用 CFile 访问文件状态](accessing-file-status.md)

*使用 MFC 序列化（对象持久性）*

- [创建可序列化类](serialization-making-a-serializable-class.md)

- [通过 CArchive 对象序列化对象](serialization-serializing-an-object.md)

- [创建 CArchive 对象](two-ways-to-create-a-carchive-object.md)

- [> 运算符使用 CArchive <\< and >](using-the-carchive-output-and-input-operators.md)

- [通过存档存储和加载 CObject 和 CObject 派生对象](storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>另请参阅

[概念](mfc-concepts.md)<br/>
[常规 MFC 主题](general-mfc-topics.md)<br/>
[CArchive 类](reference/carchive-class.md)<br/>
[CObject 类](reference/cobject-class.md)

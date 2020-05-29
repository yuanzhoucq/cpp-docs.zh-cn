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
ms.openlocfilehash: 3a99c4143bbd27ba765b0289b80be8870a940f63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365312"
---
# <a name="files-in-mfc"></a>MFC 中的文件

在 Microsoft 基础类库 （MFC） 中，类[CFile](../mfc/reference/cfile-class.md)处理常规文件 I/O 操作。 此系列文章介绍如何打开和关闭文件以及如何读取数据并将数据写入文件。 还讨论了文件状态操作。 有关如何使用 MFC 基于对象的序列化功能作为读取和写入文件中数据的替代方法的说明，请参阅文章[序列化](../mfc/serialization-in-mfc.md)。

> [!NOTE]
> 使用 MFC`CDocument`对象时，框架会为您执行大部分序列化工作。 具体而言，框架将创建和使用 `CFile` 对象。 您只需要在类`Serialize``CDocument`的成员函数的重写中编写代码。

`CFile` 类为通用二进制文件操作提供了一个接口。 派生自 `CStdioFile` 的 `CMemFile` 和 `CFile` 类以及派生自 `CSharedFile` 的 `CMemFile` 类提供了更专业的文件服务。

有关 MFC 文件处理替代方法的详细信息，请参阅*运行时库参考*中[的文件处理](../c-runtime-library/file-handling.md)。

有关派生`CFile`类的信息，请参阅[MFC 层次结构图表](../mfc/hierarchy-chart.md)。

## <a name="what-do-you-want-to-do"></a>你想做什么

*使用 CFile*

- [使用 CFile 打开文件](../mfc/opening-files.md)

- [使用 CFile 读写文件](../mfc/reading-and-writing-files.md)

- [使用 CFile 关闭文件](../mfc/closing-files.md)

- [使用 CFile 访问文件状态](../mfc/accessing-file-status.md)

*使用 MFC 序列化（对象持久性）*

- [创建可序列化类](../mfc/serialization-making-a-serializable-class.md)

- [通过 CArchive 对象序列化对象](../mfc/serialization-serializing-an-object.md)

- [创建 CArchive 对象](../mfc/two-ways-to-create-a-carchive-object.md)

- [使用 CArchive \< <和 >> 运算符](../mfc/using-the-carchive-output-and-input-operators.md)

- [通过存档存储和加载 CObject 和 CObject 派生对象](../mfc/storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>另请参阅

[概念](../mfc/mfc-concepts.md)<br/>
[一般 MFC 主题](../mfc/general-mfc-topics.md)<br/>
[CArchive 类](../mfc/reference/carchive-class.md)<br/>
[CObject 类](../mfc/reference/cobject-class.md)

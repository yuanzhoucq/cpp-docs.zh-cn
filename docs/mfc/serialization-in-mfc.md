---
title: MFC 中的序列化
ms.date: 11/04/2016
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
ms.openlocfilehash: 5c7dec140635b6d83bdae936d1bb0cef144f825b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308207"
---
# <a name="serialization-in-mfc"></a>MFC 中的序列化

本文介绍了提供在 Microsoft 基础类库 (MFC) 以允许对象之间保持不变的序列化机制在程序运行。

序列化是从永久存储媒体，如磁盘文件写入或读取到或对象的过程。 序列化是理想的情况下它想要维护结构化数据的状态 (如C++类或结构) 期间或之后执行程序。 使用 MFC 提供的序列化对象，这发生在标准且一致的方式，从而减轻用户将不再需要手动执行文件操作。

MFC 提供了对序列化的类中的内置支持`CObject`。 因此，所有类都派生自`CObject`可以充分利用`CObject`的序列化协议。

序列化的基本理念是一个对象应该能够编写其成员变量，到持久存储的值通常指示其当前状态。 更高版本，可以通过读取或反序列化对象的状态从存储重新创建该对象。 序列化处理对象指针和序列化对象时使用的对象的循环引用的所有详细的信息。 一个关键点是对象本身负责读取和写入其自己的状态。 因此，对于是可序列化的类，它必须实现的基本序列化操作。 序列化组项目中所示，很容易地将此功能添加到类。

MFC 使用的对象`CArchive`类作为要进行序列化的对象与该存储介质之间的中介。 此对象始终是与相关联`CFile`对象从其获取所需的信息进行序列化，包括文件名称和请求的操作是读取或写入。 执行序列化操作的对象可以使用`CArchive`对象而不考虑对存储介质的性质。

一个`CArchive`对象使用重载的插入 (**<\<**) 和提取 (**>>**) 运算符来执行写入和读取操作。 有关详细信息，请参阅[存储和加载 Cobject 通过存档](../mfc/storing-and-loading-cobjects-via-an-archive.md)中序列化的文章：序列化对象。

> [!NOTE]
>  不要混淆`CArchive`类与常规用途 iostream 类，用于设置纯文本格式。 `CArchive`类是二进制格式序列化对象。

如果你想，您可以绕过 MFC 序列化以创建您自己的持久性数据存储机制。 你将需要重写启动在用户的命令的序列化的类成员函数。 请参阅中的讨论[技术说明 22](../mfc/tn022-standard-commands-implementation.md) ID_FILE_OPEN、 ID_FILE_SAVE 和 ID_FILE_SAVE_AS 标准命令。

以下文章介绍了序列化所需的两个主要任务：

- [序列化：创建可序列化类](../mfc/serialization-making-a-serializable-class.md)

- [序列化：序列化对象](../mfc/serialization-serializing-an-object.md)

文章[序列化：序列化与数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)描述序列化时在数据库应用程序中适当的输入/输出方法。

## <a name="see-also"></a>请参阅

[概念](../mfc/mfc-concepts.md)<br/>
[常规 MFC 主题](../mfc/general-mfc-topics.md)<br/>
[CArchive 类](../mfc/reference/carchive-class.md)<br/>
[CObject 类](../mfc/reference/cobject-class.md)<br/>
[CDocument 类](../mfc/reference/cdocument-class.md)<br/>
[CFile 类](../mfc/reference/cfile-class.md)

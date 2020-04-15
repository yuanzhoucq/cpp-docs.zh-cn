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
ms.openlocfilehash: eca4d0357977bc7ef21063718c738ae5bd8e7431
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372751"
---
# <a name="serialization-in-mfc"></a>MFC 中的序列化

本文介绍了 Microsoft 基础类库 （MFC） 中提供的序列化机制，该机制允许对象在程序运行之间保留。

序列化是写入或读取对象到或从持久存储介质（如磁盘文件）写入或读取的过程。 序列化非常适合在程序执行期间或之后需要保持结构化数据的状态（如C++类或结构）的情况。 使用 MFC 提供的序列化对象可以以标准和一致的方式执行此操作，从而免除用户手动执行文件操作的需要。

MFC 为类`CObject`中序列化提供内置支持。 因此，派生自`CObject`的所有类都可以利用`CObject`的序列化协议。

序列化的基本思想是，对象应该能够将其当前状态（通常由其成员变量的值指示）写入持久存储。 稍后，可以通过从存储中读取或反序列化对象的状态来重新创建对象。 序列化处理对象指针和对对象序列化时使用的对象的循环引用的所有详细信息。 关键点是对象本身负责读取和写入自己的状态。 因此，要对类进行序列化，必须实现基本的序列化操作。 如文章的序列化组所示，可以轻松地将此功能添加到类中。

MFC 使用`CArchive`类的对象作为要序列化的对象和存储介质之间的中介。 此对象始终与`CFile`对象关联，从该对象获取序列化所需的信息，包括文件名以及请求的操作是读取还是写入。 执行序列化操作的对象可以使用该对象，`CArchive`而不考虑存储介质的性质。

对象`CArchive`使用重载插入 （**<**） 和**>>** 提取 （ ） 运算符来执行写入和读取操作。 有关详细信息，请参阅在"序列化：序列化"一文中[通过存档存储和加载 CObject。](../mfc/storing-and-loading-cobjects-via-an-archive.md)

> [!NOTE]
> 不要将`CArchive`类与通用 iostream 类混淆，这些类仅用于格式化文本。 该`CArchive`类适用于二进制格式的序列化对象。

如果需要，可以绕过 MFC 序列化，为持久数据存储创建自己的机制。 您需要重写在用户命令下启动序列化的类成员函数。 请参阅ID_FILE_OPEN、ID_FILE_SAVE和ID_FILE_SAVE_AS标准命令[的技术说明 22](../mfc/tn022-standard-commands-implementation.md)中的讨论。

以下文章介绍序列化所需的两项主要任务：

- [序列化：定义可序列化的类](../mfc/serialization-making-a-serializable-class.md)

- [序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)

文章[序列化：序列化与数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)描述序列化是数据库应用程序中适当的输入/输出技术。

## <a name="see-also"></a>另请参阅

[概念](../mfc/mfc-concepts.md)<br/>
[一般 MFC 主题](../mfc/general-mfc-topics.md)<br/>
[CArchive 类](../mfc/reference/carchive-class.md)<br/>
[CObject 类](../mfc/reference/cobject-class.md)<br/>
[CDocument 类](../mfc/reference/cdocument-class.md)<br/>
[CFile 类](../mfc/reference/cfile-class.md)

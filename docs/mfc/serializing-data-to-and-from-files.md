---
title: 针对文件进行数据序列化
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], serialization
- documents [MFC], saving
- saving documents
- deserialization [MFC]
- serialization [MFC], role of document
- serialization [MFC], role of data
- data [MFC]
- data [MFC], serializing
- document data [MFC]
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
ms.openlocfilehash: af3cde9445ae4b128e7e54a5f154db01b2eecd3b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279258"
---
# <a name="serializing-data-to-and-from-files"></a>针对文件进行数据序列化

暂留的基本理念是一个对象应该能够编写其成员变量，到持久存储的值指示其当前状态。 更高版本，可以通过读取，或"反序列化，"对象的状态从持久性存储区重新创建该对象。 此处的关键一点是对象本身负责读取和写入其自己的状态。 因此，对于为持久的类，它必须实现的基本序列化操作。

框架提供了用于将文档保存到磁盘文件保存到的响应中的默认实现和另存为命令和打开命令的响应中的磁盘文件中加载文档的文件菜单上。 随着工作很少，您可以实现写入和读取其数据传入和传出文件文档的功能。 必须执行的主要操作是重写[Serialize](../mfc/reference/cobject-class.md#serialize)成员函数在您的文档类。

MFC 应用程序向导会放置的主干重写`CDocument`成员函数`Serialize`中将为你创建的文档类。 在实现应用程序的成员变量后，您可以填充你`Serialize`重写，将数据发送到"存档对象"连接到一个文件的代码。 一个[CArchive](../mfc/reference/carchive-class.md)对象都类似于**cin**并**cout**输入/输出 c + + iostream 库中的对象。 但是，`CArchive`写入和读取二进制格式，而非格式化文本。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [序列化](../mfc/serialization-in-mfc.md)

- [在序列化文档的角色](#_core_the_document.92.s_role_in_serialization)

- [在序列化的数据的角色](#_core_the_data.92.s_role_in_serialization)

- [跳过序列化机制](../mfc/bypassing-the-serialization-mechanism.md)

##  <a name="_core_the_document.92.s_role_in_serialization"></a> 在序列化文档的角色

框架自动响应为文件菜单打开，保存，并将另存为命令通过调用文档的`Serialize`成员函数，如果它实现的。 ID_FILE_OPEN 命令，例如，调用处理程序函数中的应用程序对象。 在此过程中，用户将看到并响应文件打开对话框，并在框架获取用户选择的文件名。 框架将创建`CArchive`对象设置了数据加载到文档并将传递到存档`Serialize`。 框架已打开该文件。 在文档中的代码`Serialize`成员函数将读取通过存档，根据需要重新构造数据对象中的数据。 有关序列化的详细信息，请参阅文章[序列化](../mfc/serialization-in-mfc.md)。

##  <a name="_core_the_data.92.s_role_in_serialization"></a> 在序列化的数据的角色

一般情况下，类类型的数据应该能够自行序列化。 也就是说时对象传递给存档时，, 该对象应了解如何将自己写入存档以及如何从存档中读取本身。 MFC 使类可序列化以这种方式提供支持。 如果设计的类来定义数据类型和所要序列化该类型的数据时，设计用于序列化。

## <a name="see-also"></a>请参阅

[使用文档](../mfc/using-documents.md)

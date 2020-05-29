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
ms.openlocfilehash: 043ba019c6b5ad79db2cedb6314c9e65f14b14b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376936"
---
# <a name="serializing-data-to-and-from-files"></a>针对文件进行数据序列化

持久性的基本思想是，对象应该能够将其当前状态（由其成员变量的值指示）写入持久存储。 稍后，可以通过读取或"反序列化"从持久存储读取对象的状态来重新创建对象。 此处的关键点是对象本身负责读取和写入其自己的状态。 因此，要使类持久化，它必须实现基本的序列化操作。

该框架提供了一个默认实现，用于将文档保存到磁盘文件，以响应"文件"菜单上的"保存和保存为"命令，以及从磁盘文件加载文档以响应 Open 命令。 只需很少工作，即可实现文档在文件中写入和读取其数据的能力。 您必须执行的主要操作是重写文档类中的[序列化](../mfc/reference/cobject-class.md#serialize)成员函数。

MFC 应用程序向导在其为您创建的文档类中放置`CDocument`成员函数`Serialize`的骨骼覆盖。 实现应用程序的成员变量后，可以使用将数据发送到连接到文件的"存档对象"的代码填充`Serialize`重写。 [CArchive](../mfc/reference/carchive-class.md)对象类似于C++ iostream 库中的**cin**和**cout**输入/输出对象。 但是，`CArchive`写入和读取二进制格式，而不是格式化文本。

## <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [序列化](../mfc/serialization-in-mfc.md)

- [文档在序列化中的作用](#_core_the_document.92.s_role_in_serialization)

- [数据在序列化中的作用](#_core_the_data.92.s_role_in_serialization)

- [跳过序列化机制](../mfc/bypassing-the-serialization-mechanism.md)

## <a name="the-documents-role-in-serialization"></a><a name="_core_the_document.92.s_role_in_serialization"></a>文档在序列化中的作用

框架自动响应文件菜单的"打开"、"保存"和"保存为"命令，如果文档`Serialize`的成员函数已实现，则调用该函数。 例如，ID_FILE_OPEN命令调用应用程序对象中的处理程序函数。 在此过程中，用户看到并响应"文件打开"对话框，框架获取用户选择的文件名。 框架创建一个`CArchive`对象，用于将数据加载到文档中并将存档传递到`Serialize`。 框架已打开该文件。 文档`Serialize`成员函数中的代码通过存档读取数据，根据需要重建数据对象。 有关序列化的详细信息，请参阅文章[序列化](../mfc/serialization-in-mfc.md)。

## <a name="the-datas-role-in-serialization"></a><a name="_core_the_data.92.s_role_in_serialization"></a>数据在序列化中的作用

通常，类类型数据应该能够序列化自身。 也就是说，当您将对象传递到存档时，该对象应知道如何将自己写入存档以及如何从存档中读取自身。 MFC 支持以这种方式使类序列化。 如果设计一个类来定义数据类型，并且打算序列化该类型的数据，则设计序列化。

## <a name="see-also"></a>另请参阅

[使用文档](../mfc/using-documents.md)

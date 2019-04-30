---
title: 跳过序列化机制
ms.date: 11/04/2016
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
ms.openlocfilehash: 1937098de30884be327c67a698dbb0023be248bb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345204"
---
# <a name="bypassing-the-serialization-mechanism"></a>跳过序列化机制

如您所见，框架提供了一个在文件中读取和写入数据的默认方式。 通过存档对象进行序列化可满足很多应用程序的需求。 此类应用程序将文件完全读入内存，让用户更新文件，然后重新将更新的版本写入磁盘。

但是，某些应用程序对数据的操作方式差别很大，对于这些应用程序，通过存档进行序列化是不适合的。 示例包括数据库程序、仅编辑大文件的一部分的程序、写入纯文本文件的程序和共享数据文件的程序。

在这些情况下，您可以重写[Serialize](../mfc/reference/cobject-class.md#serialize)函数的不同方式调解文件操作通过[CFile](../mfc/reference/cfile-class.md)对象而非[CArchive](../mfc/reference/carchive-class.md)对象。

可以使用`Open`， `Read`， `Write`， `Close`，和`Seek`类的成员函数`CFile`若要打开一个文件，请将文件指针移动到该文件中的特定点 （查找） 读取的记录 （指定的字节数) 在这种情况下，允许用户更新的记录，然后再次查找同一点并将记录写回到文件。 框架将为您打开文件，您可以使用类 `GetFile` 的 `CArchive` 成员函数获取指向 `CFile` 对象的指针。 对于更加复杂和灵活的用法，您可以重写[OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument)并[OnSaveDocument](../mfc/reference/cdocument-class.md#onsavedocument)类的成员函数`CWinApp`。 有关详细信息，请参阅类[CFile](../mfc/reference/cfile-class.md)中*MFC 参考*。

在这种情况下，`Serialize` 重写不执行任何操作，除非您想让它在文档关闭时读取和写入文件头以使其保持最新（举例）。

## <a name="see-also"></a>请参阅

[使用文档](../mfc/using-documents.md)

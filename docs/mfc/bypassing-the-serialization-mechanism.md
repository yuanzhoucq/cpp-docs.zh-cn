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
ms.openlocfilehash: f47cac34f6cdbdae01af98ec28be5af17edf0e25
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620968"
---
# <a name="bypassing-the-serialization-mechanism"></a>跳过序列化机制

如您所见，框架提供了一个在文件中读取和写入数据的默认方式。 通过存档对象进行序列化可满足很多应用程序的需求。 此类应用程序将文件完全读入内存，让用户更新文件，然后重新将更新的版本写入磁盘。

但是，某些应用程序对数据的操作方式差别很大，对于这些应用程序，通过存档进行序列化是不适合的。 示例包括数据库程序、仅编辑大文件的一部分的程序、写入纯文本文件的程序和共享数据文件的程序。

在这些情况下，可以通过不同方式重写[序列化](reference/cobject-class.md#serialize)函数，通过[CFile](reference/cfile-class.md)对象而不是[CArchive](reference/carchive-class.md)对象来调解文件操作。

您可以使用 `Open` 类的、 `Read` 、、 `Write` `Close` 和 `Seek` 成员函数 `CFile` 打开文件，将文件指针（查找）移动到文件中的特定点，在该点读取记录（指定的字节数），让用户更新记录，然后再次查找到同一点并将记录写回文件。 框架将为您打开文件，您可以使用类 `GetFile` 的 `CArchive` 成员函数获取指向 `CFile` 对象的指针。 为了更复杂且更灵活，可以重写类的[OnOpenDocument](reference/cdocument-class.md#onopendocument)和[onopendocument](reference/cdocument-class.md#onsavedocument)成员函数 `CWinApp` 。 有关详细信息，请参阅*MFC 参考*中的[CFile](reference/cfile-class.md)类。

在这种情况下，`Serialize` 重写不执行任何操作，除非您想让它在文档关闭时读取和写入文件头以使其保持最新（举例）。

## <a name="see-also"></a>另请参阅

[使用文档](using-documents.md)

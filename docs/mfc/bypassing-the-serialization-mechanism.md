---
title: 跳过序列化机制 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9252e08fe672f111dcf2b289b1b12891022a318d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931081"
---
# <a name="bypassing-the-serialization-mechanism"></a>跳过序列化机制
如您所见，框架提供了一个在文件中读取和写入数据的默认方式。 通过存档对象进行序列化可满足很多应用程序的需求。 此类应用程序将文件完全读入内存，让用户更新文件，然后重新将更新的版本写入磁盘。  
  
 但是，某些应用程序对数据的操作方式差别很大，对于这些应用程序，通过存档进行序列化是不适合的。 示例包括数据库程序、仅编辑大文件的一部分的程序、写入纯文本文件的程序和共享数据文件的程序。  
  
 在这些情况下，你可以重写[序列化](../mfc/reference/cobject-class.md#serialize)中另一种方式调解文件操作通过函数[CFile](../mfc/reference/cfile-class.md)对象而不是[CArchive](../mfc/reference/carchive-class.md)对象。  
  
 你可以使用`Open`， `Read`， `Write`， `Close`，和`Seek`类的成员函数`CFile`若要打开的文件，移动文件指针 （查找） 到该文件中的特定点读取记录 （指定的字节数) 在该点，让用户更新的记录，然后再次的同一点查找并记录返回写入该文件。 框架将为您打开文件，您可以使用类 `GetFile` 的 `CArchive` 成员函数获取指向 `CFile` 对象的指针。 对于更复杂且灵活的使用，您可以重写[OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument)和[OnSaveDocument](../mfc/reference/cdocument-class.md#onsavedocument)类的成员函数`CWinApp`。 有关详细信息，请参阅类[CFile](../mfc/reference/cfile-class.md)中*MFC 参考*。  
  
 在这种情况下，`Serialize` 重写不执行任何操作，除非您想让它在文档关闭时读取和写入文件头以使其保持最新（举例）。  
  
## <a name="see-also"></a>请参阅  
 [使用文档](../mfc/using-documents.md)


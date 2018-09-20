---
title: 使用文档 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], C++ applications
- data [MFC], reading
- documents [MFC]
- files [MFC], writing to
- data [MFC], documents
- files [MFC]
- views [MFC], C++ applications
- document/view architecture [MFC], documents
- reading data [MFC], documents and views
- printing [MFC], documents
- writing to files [MFC]
ms.assetid: f390d6d8-d0e1-4497-9b6a-435f7ce0776c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f039b2e81b52c753a1fb065572d4eac53d55ec9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428702"
---
# <a name="using-documents"></a>使用文档

在同时工作，文档和视图：

- 包含、 管理和显示您的应用程序特定[数据](../mfc/managing-data-with-document-data-variables.md)。

- 提供的接口组成[文档数据变量](../mfc/managing-data-with-document-data-variables.md)数据。

- 参与[写入和读取文件](../mfc/serializing-data-to-and-from-files.md)。

- 参与[打印](../mfc/role-of-the-view-in-printing.md)。

- [处理](../mfc/handling-commands-in-the-document.md)的大多数应用程序的命令和消息。

文档是特别涉及到管理数据。 将你的数据，通常情况下，存储在文档类成员变量。 视图使用这些变量来访问所显示数据的和更新。 文档的默认序列化机制管理读取和写入数据，向 / 从文件。 命令 （但不是 WM_COMMAND 的其他 Windows 消息），还可以处理的文档。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [从 CDocument 派生文档类](../mfc/deriving-a-document-class-from-cdocument.md)

- [使用文档数据变量管理数据](../mfc/managing-data-with-document-data-variables.md)

- [序列化数据传入和传出文件](../mfc/serializing-data-to-and-from-files.md)

- [跳过序列化机制](../mfc/bypassing-the-serialization-mechanism.md)

- [处理文档中的命令](../mfc/handling-commands-in-the-document.md)

- [OnNewDocument 成员函数](../mfc/reference/cdocument-class.md#onnewdocument)

- [DeleteContents 成员函数](../mfc/reference/cdocument-class.md#deletecontents)

## <a name="see-also"></a>请参阅

[文档/视图体系结构](../mfc/document-view-architecture.md)


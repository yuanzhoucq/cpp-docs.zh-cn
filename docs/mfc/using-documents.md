---
title: "使用文档 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 691d8d00b9c4671ea4b9c318313851a7fab73f7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-documents"></a>使用文档
在同时工作，文档和视图：  
  
-   包含、 管理和显示您的应用程序特定[数据](../mfc/managing-data-with-document-data-variables.md)。  
  
-   提供接口组成[文档数据变量](../mfc/managing-data-with-document-data-variables.md)用于操作数据。  
  
-   参与[写入和读取文件](../mfc/serializing-data-to-and-from-files.md)。  
  
-   参与[打印](../mfc/role-of-the-view-in-printing.md)。  
  
-   [处理](../mfc/handling-commands-in-the-document.md)大部分应用程序的命令和消息。  
  
 文档是特别管理所涉及的数据。 将你的数据，通常情况下，存储在文档类成员变量。 该视图使用这些变量来访问数据以用于显示和更新。 文档的默认序列化机制管理读取和写入数据，与其他文件。 文档还可以处理命令 (但不是 Windows 消息以外**WM_COMMAND**)。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [从 CDocument 派生文档类](../mfc/deriving-a-document-class-from-cdocument.md)  
  
-   [使用文档数据变量管理数据](../mfc/managing-data-with-document-data-variables.md)  
  
-   [序列化的数据传入和传出文件](../mfc/serializing-data-to-and-from-files.md)  
  
-   [跳过序列化机制](../mfc/bypassing-the-serialization-mechanism.md)  
  
-   [处理文档中的命令](../mfc/handling-commands-in-the-document.md)  
  
-   [OnNewDocument 成员函数](../mfc/reference/cdocument-class.md#onnewdocument)  
  
-   [DeleteContents 成员函数](../mfc/reference/cdocument-class.md#deletecontents)  
  
## <a name="see-also"></a>请参阅  
 [文档/视图体系结构](../mfc/document-view-architecture.md)


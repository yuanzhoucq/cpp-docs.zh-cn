---
title: "跳过序列化机制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "存档对象 [C++]"
  - "存档 [C++]"
  - "存档 [C++], 序列化"
  - "跳过序列化"
  - "序列化 [C++], 跳过"
  - "序列化 [C++], 重写"
  - "序列化 [C++], 框架的角色"
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 跳过序列化机制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如您所见，框架提供一个默认方式在文件中读取和写入数据。  通过归档对象序列化满足许多应用程序的需要。  这样的应用程序将文件完全读取到内存，让用户更新文件，然后重新将更新版本写入到磁盘。  
  
 但是，一些应用程序在数据上的操作非常不同，对于这些应用程序通过将序列化是不适合的。  示例数据库编程，编辑大文件一部分的编程，写纯文本文件编程和程序共享的数据文件编程。  
  
 在这些情况下，您可以用不同的方式重写函数 [Serialize](../Topic/CObject::Serialize.md) 通过 [CFile](../mfc/reference/cfile-class.md) 对象干预文件操作而不是 [CArchive](../mfc/reference/carchive-class.md) 对象。  
  
 可以使用 `CFile` 类的 **Open**， **Read**， **Write**， **Close** 和 `Seek` 成员函数类打开文件，移动文件指针 \(seek （跟踪）\) 到文件中某个特定点，在该点读取记录 \(指定的字节数\)，允许用户更新记录，然后再查找到同一点并将记录写回文件。  框架将打开文件，您可以使用 `CArchive` 类的 `GetFile` 成员函数获取指向 `CFile` 对象的指针。  对于更复杂且灵活的使用，可以重写 `CWinApp` 类的 [OnSaveDocument](../Topic/CDocument::OnSaveDocument.md) 和 [OnOpenDocument](../Topic/CDocument::OnOpenDocument.md) 成员函数。  有关更多信息，请参见 *MFC 参考* 中的 [CFile](../mfc/reference/cfile-class.md) 类。  
  
 在这种方案中，重写 `Serialize` 没有，除非，如，在关闭文档时使用它读取和写入文件标头以保持其最新。  
  
## 请参阅  
 [使用文档](../mfc/using-documents.md)
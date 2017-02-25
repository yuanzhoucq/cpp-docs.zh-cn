---
title: "MFC 中的文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "二进制访问"
  - "二进制访问, MFC 中的二元文件运算"
  - "文件 I/O 类 [C++]"
  - "文件 [C++], 操作"
  - "文件 [C++], MFC"
  - "文件 [C++], 序列化"
  - "I/O [C++], MFC 类"
  - "I/O [MFC]"
  - "MFC [C++], 文件操作"
  - "持久性 [C++]"
  - "序列化 [C++], MFC 文件"
ms.assetid: ae25e2c5-2859-4679-ab97-438824e93ce1
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# MFC 中的文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Microsoft 基础类库 \(MFC\)，[CFile](../mfc/reference/cfile-class.md) 类常规处理文件 I\/O 操作。  此系列文章解释如何打开和关闭文件以及读取和写入数据。  还讨论文件状态操作。  有关阐释使用 MFC 的方式基于对象的序列化功能作为读取和写入数据一个替代方法在文件，请参见的文章 [序列化](../mfc/serialization-in-mfc.md)。  
  
> [!NOTE]
>  当使用 MFC **CDocument** 对象时，框架序列化您完成大部分工作。  特别是，框架创建和使用 `CFile` 对象。  必须仅编写在 **CDocument**类的 `Serialize` 成员函数的重写代码。  
  
 `CFile` 类为泛二进制文件操作提供一个接口。  从 `CFile` 派生的 `CStdioFile` 和 `CMemFile` 类以及从 `CMemFile` 派生的 `CSharedFile` 类通知提供专用文件服务。  
  
 有关指向处理 MFC 的文件选择的更多信息，请参见位于 *运行库引用的*[文件处理](../c-runtime-library/file-handling.md)。  
  
 有关派生的 `CFile` 类的信息，请参见 [MFC 层次结构关系图](../mfc/hierarchy-chart.md)。  
  
## 你希望做什么？  
 *使用 C 文件*  
  
-   [用CFile打开文件](../mfc/opening-files.md)  
  
-   [读写与 C 文件的文件](../mfc/reading-and-writing-files.md)  
  
-   [关闭具有 C 文件的文件](../mfc/closing-files.md)  
  
-   [访问带有 C 文件的状态](../mfc/accessing-file-status.md)  
  
 *使用 MFC \(序列化对象持久性\)*  
  
-   [创建一个可序列化类](../mfc/serialization-making-a-serializable-class.md)  
  
-   [通过 CArchive 对象序列化对象](../mfc/serialization-serializing-an-object.md)  
  
-   [创建一个新的CArchive对象。](../mfc/two-ways-to-create-a-carchive-object.md)  
  
-   [使用 CArchive \<\< 和 \>\> 运算符](../mfc/using-the-carchive-output-and-input-operators.md)  
  
-   [通过存储 CObjects 存档并加载和 CObject 派生的对象](../mfc/storing-and-loading-cobjects-via-an-archive.md)  
  
## 请参阅  
 [概念](../mfc/mfc-concepts.md)   
 [常规 MFC 主题](../mfc/general-mfc-topics.md)   
 [CArchive Class](../mfc/reference/carchive-class.md)   
 [CObject Class](../mfc/reference/cobject-class.md)   
 [如何：使用 C 文件类？](http://go.microsoft.com/fwlink/?LinkId=128046)
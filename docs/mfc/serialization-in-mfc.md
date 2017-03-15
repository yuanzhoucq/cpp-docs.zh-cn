---
title: "MFC 中的序列化 | Microsoft Docs"
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
  - "跳过序列化"
  - "集合类, 序列化"
  - "MFC, 序列化"
  - "序列化 [C++], 跳过"
  - "序列化 [C++], MFC"
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# MFC 中的序列化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文演示 Microsoft 基础类库 \(MFC\) 提供的序列化机制使对象保持不变。程序运行之间。  
  
 序列化是写入或读取对象进程出入持久性存储媒体 \(如磁盘文件。  序列化负责维护有关结构化数据状态的情况是需要 \(如 C\+\+ 类或结构在程序过程中\)，将执行。  使用 MFC 提供的序列化对象允许此目的一种标准和一致的情况下，欣慰用户从需要手动执行文件操作。  
  
 MFC 提供序列化的内置支持。`CObject`类。  因此，任何从 `CObject` 派生的类可以使用 `CObject` 序列化协议。  
  
 序列化本意是对象应该能够将其当前状态写入，通常表示由的值成员变量，与持久性存储区。  之后，对象可以通过读取或反序列化对象的状态，重新创建从存储的。  处理序列化对象指针到任何使用的对象的详细信息和循环引用，当序列化对象时。  关键是对象为读取和编写自己的运行状态。  因此，用于类的可序列化，它必须实现基本序列化操作。  如本文的序列化组所示，添加此功能很容易。类。  
  
 MFC 使用 `CArchive` 类的对象，该对象将在序列化和存储介质存储之间的中间。  此对象始终与 `CFile` 对象序列化，它包含必要的信息，包括文件名，然后请求操作是否是读取或写入。  执行序列化操作的对象可以使用 `CArchive` 对象而不考虑存储媒介的性质。  
  
 `CArchive` 对象使用了重载的插入 \(**\<\<**\) 和提取 \(**\>\>**\) 运算符执行文本和读取操作。  有关更多信息，请参见中序列化的文章 [存储和加载的 CObjects 通过存档](../mfc/storing-and-loading-cobjects-via-an-archive.md) :序列化对象。  
  
> [!NOTE]
>  请勿与 `CArchive` 类相混淆 iostream 泛型类，用于仅格式化文本。  `CArchive` 类是用于二进制格式序列化的对象。  
  
 如果希望，可以跳过 MFC 序列化创建自己的持久性数据存储的机制。  需要重写成员函数启动该序列化在用户命令的类。  参见 `ID_FILE_OPEN`、**ID\_FILE\_SAVE**和 **ID\_FILE\_SAVE\_AS** 命令标准的 [技术说明 22](../mfc/tn022-standard-commands-implementation.md) 的讨论。  
  
 下列文章中的序列化所需的两项主要任务：  
  
-   [序列化：类进行序列化](../mfc/serialization-making-a-serializable-class.md)  
  
-   [序列化：序列化对象](../mfc/serialization-serializing-an-object.md)  
  
 文章 [序列化：序列化与输入\/输出数据库](../mfc/serialization-serialization-vs-database-input-output.md) 描述序列化时是在数据库应用程序中合适性能的技术。  
  
## 请参阅  
 [概念](../mfc/mfc-concepts.md)   
 [常规 MFC 主题](../mfc/general-mfc-topics.md)   
 [CArchive Class](../mfc/reference/carchive-class.md)   
 [CObject Class](../mfc/reference/cobject-class.md)   
 [CDocument Class](../mfc/reference/cdocument-class.md)   
 [CFile Class](../mfc/reference/cfile-class.md)
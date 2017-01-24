---
title: "针对文件进行数据序列化 | Microsoft Docs"
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
  - "数据 [MFC]"
  - "数据 [MFC], 序列化"
  - "反序列化 [C++]"
  - "文档数据 [C++]"
  - "文档 [C++], 保存"
  - "文档 [C++], 序列化"
  - "保存文档"
  - "序列化 [C++], 数据的角色"
  - "序列化 [C++], 文档的角色"
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 针对文件进行数据序列化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

持久性本意是对象应该能够将其当前状态写入，表示由的值成员变量，与持久性存储区。  之后，对象可以通过读取或“反序列化重新创建，”fr 永久性存储对象的状态。  此处的关键对象是用于读取和编写自己的运行状态。  因此，为的类可以是不可变的，则它必须实现基本序列化操作。  
  
 框架提供保存文档提供默认实现。磁盘文件根据保存，并且另存为"命令"菜单以及从磁盘文件中加载的文档根据打开命令。  很少个工作，可实现文档的能力进出文件读取和写入数据。  必须执行的基本事件重写是文档中的 [序列化](../Topic/CObject::Serialize.md) 类成员函数。  
  
 MFC 应用程序向导。类文档将为您创建 **CDocument** 成员函数 `Serialize` 的骨骼重写。  在实现了应用程序的成员变量后，您可以将数据发送到”连接的“Archive 对象对文件的代码的 `Serialize` 重写。  [CArchive](../mfc/reference/carchive-class.md) 对象类似于 C\+\+ iostream 库的输入\/输出的 `cin` 和 `cout` 对象。  但是，并读取 `CArchive` 写入二进制格式，非格式化文本。  
  
## 您想进一步了解什么？  
  
-   [序列化](../mfc/serialization-in-mfc.md)  
  
-   [在序列化的文档。](#_core_the_document.92.s_role_in_serialization)  
  
-   [在序列化数据的效果](#_core_the_data.92.s_role_in_serialization)  
  
-   [对于序列化机制](../mfc/bypassing-the-serialization-mechanism.md)  
  
##  <a name="_core_the_document.92.s_role_in_serialization"></a> 在序列化的文档。  
 框架将自动响应"文件"菜单中打开，保存并"另存为"命令通过调用文档的 `Serialize` 成员函数。是否已实现。  `ID_FILE_OPEN` 命令，例如，调用在应用程序对象的处理程序函数。  在此过程中，用户看到并响应文件打开对话框，而框架获取用户选择的文件。  框架创建加载数据的 `CArchive` 对象设置到文档并将存档到 `Serialize`。  框架已打开的文件。  在文档的 `Serialize` 成员函数中的代码。存档写入数据，根据需要重新生成数据对象。  有关序列化的更多信息，请参见知识库文章 [序列化](../mfc/serialization-in-mfc.md)。  
  
##  <a name="_core_the_data.92.s_role_in_serialization"></a> 在序列化数据的效果  
 通常，类类型数据应可以序列化。  也就是说，当传递到存档对象时，对象应该知道如何编写读取到一个存档和存档。  MFC 为使得类提供支持可序列化。  如果您设计一类定义数据类型，并且打算序列化该类型数据，用于序列化中设计。  
  
## 请参阅  
 [使用文档](../mfc/using-documents.md)
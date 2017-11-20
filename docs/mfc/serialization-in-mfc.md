---
title: "MFC 中的序列化 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d5c60fd4ff47745e5209023783b74f52a319065d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="serialization-in-mfc"></a>MFC 中的序列化
此文章介绍了提供在 Microsoft 基础类库 (MFC) 以允许对象之间保持不变的序列化机制运行的程序。  
  
 序列化是从持久性存储介质，例如磁盘文件写入或读取到或对象的过程。 序列化非常适合于最好维持的状态的结构化数据 （例如 c + + 类或结构） 期间或之后执行程序的情况。 使用 MFC 提供的序列化对象，这一目的以标准且一致的方式，这使无需手动执行文件操作的用户。  
  
 MFC 提供了对类中的序列化的内置支持`CObject`。 因此，所有类都派生自`CObject`可以充分利用`CObject`的序列化协议。  
  
 序列化的基本理念都是一个对象应该能够编写其成员变量，到持久存储的值通常指示其当前状态。 以后，可以通过读取，或反序列化对象的状态从存储重新创建该对象。 序列化处理对象指针和序列化对象时使用的对象的循环引用的所有详细的信息。 关键点是对象本身负责读取和写入其自己的状态。 因此，对于是可序列化的类，它必须实现的基本序列化操作。 序列化系列文章中所示，很容易向类添加此功能。  
  
 MFC 使用的对象`CArchive`类作为对象要序列化和存储介质的中介。 此对象始终是与关联`CFile`对象，它获取用于序列化，包括文件名称的必要信息以及请求的操作是读取或写入。 执行序列化操作的对象可以使用`CArchive`对象而不考虑存储介质的性质。  
  
 A`CArchive`对象使用重载的插入 (**<\<**) 和提取 (**>>**) 运算符执行写入和读取操作。 有关详细信息，请参阅[存储和加载 Cobject 通过存档](../mfc/storing-and-loading-cobjects-via-an-archive.md)本文序列化： 序列化对象。  
  
> [!NOTE]
>  不要混淆`CArchive`类通用 iostream 类，该类适用于格式化纯文本。 `CArchive`类是的二进制格式序列化对象。  
  
 如果你想，你可以绕过 MFC 序列化以创建自己的永久数据存储区的机制。 你将需要重写启动在用户的命令的序列化的类成员函数。 请参阅中的讨论[技术说明 22](../mfc/tn022-standard-commands-implementation.md)的`ID_FILE_OPEN`， **ID_FILE_SAVE**，和**ID_FILE_SAVE_AS**标准命令。  
  
 以下文章介绍序列化所需的两个主要任务：  
  
-   [序列化：定义可序列化的类](../mfc/serialization-making-a-serializable-class.md)  
  
-   [序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)  
  
 文章[序列化： 序列化 vs。数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)描述当序列化是一种适当的输入/输出技术，数据库应用程序中。  
  
## <a name="see-also"></a>另请参阅  
 [概念](../mfc/mfc-concepts.md)   
 [常规 MFC 主题](../mfc/general-mfc-topics.md)   
 [CArchive 类](../mfc/reference/carchive-class.md)   
 [CObject 类](../mfc/reference/cobject-class.md)   
 [CDocument 类](../mfc/reference/cdocument-class.md)   
 [CFile 类](../mfc/reference/cfile-class.md)

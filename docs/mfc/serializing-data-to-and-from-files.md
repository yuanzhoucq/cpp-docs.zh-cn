---
title: "进行数据序列化到文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], serialization
- documents [MFC], saving
- saving documents
- deserialization [MFC]
- serialization [MFC], role of document
- serialization [MFC], role of data
- data [MFC]
- data [MFC], serializing
- document data [MFC]
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d28b12e19b302f5576d2cd76c931e0036c208185
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="serializing-data-to-and-from-files"></a>针对文件进行数据序列化
持久性基本理念都是一个对象应该能够编写其成员变量，到持久存储的值指示其当前状态。 以后，可以通过读取，或"反序列化，"对象的状态从持久性存储区重新创建该对象。 此处关键的一点是对象本身负责读取和写入其自己的状态。 因此，对于类为永久，它必须实现的基本序列化操作。  
  
 该框架提供的默认实现，将文档保存到磁盘文件以响应保存和另存为命令在文件菜单上以及为从打开命令的响应中的磁盘文件中加载的文档。 非常轻易地，你可以实现写入和读取其数据传入和传出文件的文档的能力。 必须执行的主要操作是覆盖[序列化](../mfc/reference/cobject-class.md#serialize)成员函数在您的文档类。  
  
 MFC 应用程序向导将放的主干重写**CDocument**成员函数`Serialize`中它为你创建的文档类。 在实现应用程序的成员变量之后，你可以在中填写你`Serialize`重写替换为将数据发送到"存档对象"连接到文件的代码。 A [CArchive](../mfc/reference/carchive-class.md)对象都类似于`cin`和`cout`输入/输出 c + + iostream 库中的对象。 但是，`CArchive`写入和读取二进制格式，不带格式的文本。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [序列化](../mfc/serialization-in-mfc.md)  
  
-   [序列化中的文档的角色](#_core_the_document.92.s_role_in_serialization)  
  
-   [在序列化的数据的角色](#_core_the_data.92.s_role_in_serialization)  
  
-   [跳过序列化机制](../mfc/bypassing-the-serialization-mechanism.md)  
  
##  <a name="_core_the_document.92.s_role_in_serialization"></a>序列化中的文档的角色  
 框架自动响应文件菜单打开、 保存，并将另存为命令通过调用文档的`Serialize`成员函数，如果它实现的。 `ID_FILE_OPEN`命令，例如，调用处理程序函数中的应用程序对象。 在此过程中，用户将看到并响应文件打开的对话框中，并 framework 获取用户选择的文件名。 框架创建`CArchive`对象设置为将数据加载到文档并将传递到存档`Serialize`。 框架已打开该文件。 在文档中的代码`Serialize`成员函数将读取通过存档，根据需要重新构造数据对象中的数据。 有关序列化的详细信息，请参阅文章[序列化](../mfc/serialization-in-mfc.md)。  
  
##  <a name="_core_the_data.92.s_role_in_serialization"></a>在序列化的数据的角色  
 通常情况下，类类型数据应该能够序列化本身。 即时到存档中传递的对象，该对象应了解本身写入存档以及如何从存档读取本身。 MFC 使类可序列化以这种方式提供支持。 如果设计用于定义数据类型的类和你想要序列化该类型的数据时，设计用于序列化。  
  
## <a name="see-also"></a>请参阅  
 [使用文档](../mfc/using-documents.md)


---
title: "存储和加载 Cobject 通过存档 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 987f754ccdf03e5a252feae693a1f7718da1b353
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>通过存档存储和加载 CObject
存储和加载`CObject`s 通过存档需要额外考虑。 在某些情况下，应调用`Serialize`函数的对象，其中`CArchive`对象是参数的`Serialize`调用，而不是使用 **< \<** 或 **>>** 运算符的`CArchive`。 需要牢记的重要事实是， `CArchive`  **>>** 运算符构造`CObject`在内存中基于`CRuntimeClass`以前由存储存档写入到文件的信息。  
  
 因此，是否使用`CArchive`  **< \<** 和 **>>** 运算符，而不是调用`Serialize`，取决于是否你*需要*加载存档以动态地重新构造对象基于以前存储`CRuntimeClass`信息。 使用`Serialize`函数在以下情况：  
  
-   当反序列化对象，你事先知道确切的类的对象。  
  
-   当反序列化对象，你已有为其分配的内存。  
  
> [!CAUTION]
>  如果你加载对象使用`Serialize`函数，您还必须存储对象使用`Serialize`函数。 不要将存储使用`CArchive`  **<<** 运算符，然后负载使用`Serialize`函数，或使用存储`Serialize`函数，然后加载使用**CArchive >>**运算符。  
  
 下面的示例阐释了这些情况：  
  
 [!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]  
  
 [!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]  
  
 总之，如果可序列化类定义一个嵌入**CObjec**t 作为成员，你应该*不*使用`CArchive`  **< \<** 和 **>>** 运算符为该对象，但应调用`Serialize`函数。 此外，如果可序列化类定义的指针`CObject`(或从派生的对象`CObject`) 作为成员，但构造此其他对象在其自己的构造函数，你还应调用`Serialize`。  
  
## <a name="see-also"></a>请参阅  
 [序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)


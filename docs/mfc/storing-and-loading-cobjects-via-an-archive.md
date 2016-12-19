---
title: "通过存档存储和加载 CObject | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive 类, 存储和加载对象"
  - "CObject 类, CArchive 对象"
  - "CObjects"
  - "CObjects, 通过存档加载"
  - "Serialize 方法, 与 CArchive 运算符"
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 通过存档存储和加载 CObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

存储和加载的 `CObject`s 和存档需要通过额外的注意事项。  在某些情况下，您应调用对象的 `Serialize` 函数，`CArchive` 对象是 `Serialize` 调用参数，而不是使用 `CArchive`的 **\<\<** 或 **\>\>** 运算符相反。  需要谨记的重要情况为 `CArchive` **\>\>** 运算符构造在根据 `CRuntimeClass` 信息内存的 `CObject` 以前写入文件由存储的存档。  
  
 因此，无论是使用 `CArchive` **\<\<**，然后 **\>\>** 运算符，与调用 `Serialize`，确定是否 *需要* 将存档动态地重新构造基于以前存储的信息的 `CRuntimeClass` 对象。  在 `Serialize` 例子中，添加以下函数：  
  
-   将反序列化对象，则预先知道对象的具体类。  
  
-   将反序列化对象时，已经为其分配的内存。  
  
> [!CAUTION]
>  使用 `Serialize` 函数，则加载对象，使用 `Serialize` 函数，还必须存储对象。  使用 `Serialize` 函数，使用 **CArchive \>\>** 运算符，请不要使用 `CArchive` 存储**\<\<** 运算符然后加载要或存储然后加载要使用 `Serialize` 函数。  
  
 以下示例演示了该例子。  
  
 [!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/CPP/storing-and-loading-cobjects-via-an-archive_1.h)]  
  
 [!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/CPP/storing-and-loading-cobjects-via-an-archive_2.cpp)]  
  
 总之，序列化定义了，则类嵌入的 t 为 **CObjec**成员，则 *不*应为该对象使用 `CArchive` **\<\<** 和 **\>\>** 运算符，而应调用 `Serialize` 函数。  此外，如果可序列化，类定义一个指向 `CObject` \(或从 `CObject`派生的对象。\) 为成员，即，但构造在其自己的构造函数，因此上述其他对象还应调用 `Serialize`。  
  
## 请参阅  
 [序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)
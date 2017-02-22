---
title: "序列化：对象的序列化 | Microsoft Docs"
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
  - "对象 [C++], 序列化"
  - "序列化 [C++], 对象"
  - "序列化对象 [C++]"
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 序列化：对象的序列化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文章 [序列化：类进行序列化](../mfc/serialization-making-a-serializable-class.md) 演示如何使类可序列化。  一旦具有了序列化类，可以在别处文件序列化该类对象通过 [CArchive](../mfc/reference/carchive-class.md) 对象。  本文说明：  
  
-   [什么是 CArchive 对象 \(MFC\)](../mfc/what-is-a-carchive-object.md)。  
  
-   [创建 CArchive 对象的两种方法](../mfc/two-ways-to-create-a-carchive-object.md)。  
  
-   [如何使用 CArchive \<\< 和 \>\> 运算符](../mfc/using-the-carchive-output-and-input-operators.md)。  
  
-   [通过存档存储和加载 CObject \(MFC\)](../mfc/storing-and-loading-cobjects-via-an-archive.md)。  
  
 可以让框架创建文档序列化的存档或显式创建 `CArchive` 对象。  可以传输数据。文件和使用的 \<\< 是 `CArchive` 对象和 \>\> 运算符之间或，在某些情况下，通过调用 `CObject`的 `Serialize` 函数的派生类。  
  
## 请参阅  
 [序列化](../mfc/serialization-in-mfc.md)
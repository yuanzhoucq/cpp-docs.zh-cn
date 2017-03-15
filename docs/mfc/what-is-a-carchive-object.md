---
title: "什么是 CArchive 对象 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CArchive"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "存档对象 [C++]"
  - "存档 [C++], 用于序列化"
  - "缓冲, 可序列化对象"
  - "缓冲区, 可序列化对象"
  - "CArchive 类, 关于 CArchive 类"
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 什么是 CArchive 对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CArchive` 对象提供用于编写类型安全机制或缓冲出入 `CFile` 中读取的可序列化对象。  `CFile` 对象通常表示磁盘文件；但是，也可以是内存文件 \(`CSharedFile` 对象\)，则可能表示剪贴板。  
  
 特定 `CArchive` 对象存储 \(写入，序列化数据\) 或加载 \(读取，反序列化\) 数据，但是，永远不两个。  `CArchive` 对象的生命限于一次写入文件或对象读取对象从文件。  因此，需要两个连续创建的 `CArchive` 对象序列化到数据文件并从文件反序列化其。  
  
 当存储到存档文件对象时，将 `CRuntimeClass` 名称 Archive 为对象。  然后，同时，另的存档加载对象从文件到内存，`CObject`派生对象都会动态地重新构造基于对象的 `CRuntimeClass`。  在写入文件由存储的存档，特定对象可能多次引用。  存档加载，不过，只有一次重新生成对象。  有关存档方式的详细信息 `CRuntimeClass` 附加信息。对象重新生成对象，并考虑可能的多个引用，在 [技术说明 2](../mfc/tn002-persistent-object-data-format.md)中描述。  
  
 当序列化数据存档到存档，累计数据，直至其缓冲区已满。  然后将其存档缓冲区为点 `CArchive` 对象为 `CFile` 对象。  同样，当您读取从存档的数据，则文件读取到其缓冲区则从缓冲区向序列化对象。  此缓冲减少硬盘实际读取的次数，从而提高应用程序的性能。  
  
## 请参阅  
 [序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)
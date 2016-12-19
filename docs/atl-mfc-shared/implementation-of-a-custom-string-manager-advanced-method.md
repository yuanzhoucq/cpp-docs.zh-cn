---
title: "Implementation of a Custom String Manager (Advanced Method) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAtlStringMgr class, using"
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementation of a Custom String Manager (Advanced Method)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在专用的情况下，您可能希望实现不仅仅用于更改堆分配内存的自定义字符串管理器。  在这种情况下，必须手动实现 [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) 接口为自定义字符串管理器。  
  
 为此，了解 [CStringT](../atl-mfc-shared/reference/cstringt-class.md) 使用该接口管理其字符串数据如何先非常重要。  `CStringT` 每个实例都有指向 [CStringData](../atl-mfc-shared/reference/cstringdata-class.md) 结构。  此可变长度结构包含有关该字符串的重要信息\(例如长度\)，以及该字符串的实际字符数据。  每个自定义字符串管理器来分配和释放这些结构根据 `CStringT`请求。  
  
 `CStringData` framework包括四个字段:  
  
-   [pStringMgr](../Topic/CStringData::pStringMgr.md) 此字段指向 `IAtlStringMgr` 用于的接口管理此字符串数据。  当 `CStringT` 需要重新分配或释放字符串缓冲区调用重新分配或释放此接口方法，通过 `CStringData` 结构作为参数。  在将在字符串管理器中 `CStringData` 结构，则必须将此字段以指向您的自定义字符串管理器。  
  
-   [nDataLength](../Topic/CStringData::nDataLength.md) 此字段包含在除终止null的缓冲区存储的字符串的当前逻辑长度。  当字符串的长度更改时，`CStringT` 更新此字段。  在将 `CStringData` 结构，则字符串经理必须设置了此字段为零。  当重新 `CStringData` 结构时，您的自定义字符串经理必须将此字段不变。  
  
-   [nAllocLength](../Topic/CStringData::nAllocLength.md) 此字段包含在此字符串缓冲区可以存储，而无需重新指派的最大字符数\(不包括终止null）。  每当 `CStringT` 需要增大该字符串，它的逻辑长度首先检查此字段确定存在缓冲区中的足够的空间。  如果检查失败，`CStringT` 对您的自定义字符串管理器重新分配缓冲区。  当分配或重新分配 `CStringData` 结构，则必须将此字段添加到 **nChars** 参数请求的字符的至少位数。[IAtlStringMgr::Allocate](../Topic/IAtlStringMgr::Allocate.md) 或 [IAtlStringMgr::Reallocate](../Topic/IAtlStringMgr::Reallocate.md)。  如果与请求对缓冲区的更多的空间，可以将此值以反映可用实际的空间量。  它必须调用返回字符串管理器重新分配缓冲区之前，这样 `CStringT` 存在该字符串填充整个分配空间。  
  
-   [nRefs](../Topic/CStringData::nRefs.md) 此字段包含当前引用字符串缓冲区的计数。  如果该值为一个，则 `CStringT` 一个实例使用缓冲。  此外，实例允许访问读取和修改缓冲区的内容。  如果值大于绝好，`CStringT` 多个实例可以使用缓冲。  由于字符缓冲区共享，`CStringT` 实例只能读取缓冲区的内容。  若要修改内容，`CStringT` 首先制作缓冲区。  如果该值为负，因此，只有 `CStringT` 一个实例使用缓冲。  在这种情况下，缓冲区被视为锁定。  当 `CStringT` 实例使用时不锁定的缓冲区 `CStringT` 其他实例可以共享缓冲区。  相反，这些情况在操作内容之前创建缓冲区的副本。  此外，使用锁定缓冲区的 `CStringT` 实例不会尝试共享其他 `CStringT` 实例缓冲区中的连接字符串。  在这种情况下，`CStringT` 实例复制另一个字符串。锁定的缓冲区。  
  
     在将 `CStringData` 结构，则必须将此字段反映出共享中的类型类中的缓冲区。  对于大多数实现，将该值设置为一个。  这允许共享行为的常用复制在写入。  但是，因此，如果您的字符串管理器不支持共享字符串缓冲区，设置此字段设置为锁定状态。  这可以强制 `CStringT` 为其分配 `CStringT` 的实例只能将此缓冲区。  
  
## 请参阅  
 [Memory Management with CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
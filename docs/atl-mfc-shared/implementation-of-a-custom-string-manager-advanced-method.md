---
title: "实现的自定义字符串管理器 （高级方法） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e76edc65e5f30fee90f346d5434ecbee320a37a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="implementation-of-a-custom-string-manager-advanced-method"></a>实现的自定义字符串管理器 （高级方法）
在特殊情况下，你可能想要实现自定义字符串管理器以外的其他更改使用的堆分配内存。 在此情况下，你必须手动实现[IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md)作为自定义字符串经理的接口。  
  
 为了执行此操作，务必要先了解如何[CStringT](../atl-mfc-shared/reference/cstringt-class.md)使用该接口来管理其字符串数据。 每个实例`CStringT`有指向的[CStringData](../atl-mfc-shared/reference/cstringdata-class.md)结构。 此长度可变的结构以及字符串的实际字符数据包含有关 （例如长度），字符串的重要信息。 每个自定义字符串管理器负责分配和释放在请求时这些结构`CStringT`。  
  
 `CStringData`结构包含四个字段：  
  
-   [pStringMgr](../atl-mfc-shared/reference/cstringdata-class.md#pstringmgr)此字段将指向`IAtlStringMgr`用于管理此字符串数据的接口。 当`CStringT`需要重新分配或释放它调用的重新分配或可用方法的此接口，传递的字符串缓冲区`CStringData`作为参数的结构。 分配时`CStringData`结构中字符串管理器中，必须设置此字段为指向你的自定义字符串的经理。  
  
-   [nDataLength](../atl-mfc-shared/reference/cstringdata-class.md#ndatalength)此字段包含不包括终止 null 的缓冲区中存储的字符串的当前逻辑长度。 `CStringT`字符串的长度更改时，请更新此字段。 分配时`CStringData`结构，字符串 manager 必须将此字段设置为零。 当重新分配`CStringData`结构，你的自定义字符串 manager 必须将此字段保持不变。  
  
-   [nAllocLength](../atl-mfc-shared/reference/cstringdata-class.md#nalloclength)此字段包含的最大 （不包括终止 null） 可以在不重新分配它的情况下存储在此字符串缓冲区中的字符数。 每当`CStringT`需要增加逻辑字符串的长度，它首先检查此字段以确保在缓冲区中没有足够的空间。 如果检查失败，`CStringT`调入你的自定义字符串的经理，以重新分配缓冲区。 当分配或重新分配`CStringData`结构，你必须将其设置字段到至少请求中的字符数**nChars**参数[IAtlStringMgr::Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#allocate)或[IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate)。 如果不是请求的缓冲区中没有更多空间，你可以设置此值以反映实际可用空间量。 这允许`CStringT`增长字符串来填充整个已有将回调到要重新分配缓冲区的字符串管理器之前，已分配空间。  
  
-   [nRefs](../atl-mfc-shared/reference/cstringdata-class.md#nrefs)此字段包含字符串缓冲区的当前引用计数。 如果值为一个，然后的单个实例`CStringT`使用的缓冲区。 此外，该实例被允许读取和修改缓冲区的内容。 如果值为大于 1 的多个实例`CStringT`可以使用缓冲区。 由于可共享的字符缓冲区，`CStringT`实例只能读取缓冲区的内容。 若要修改的内容，`CStringT`首先使该缓冲区的副本。 如果值为负，只有一个实例`CStringT`使用的缓冲区。 在这种情况下，缓冲区被视为锁定。 当`CStringT`实例使用锁定的缓冲区的任何其他实例`CStringT`可能会共享缓冲区。 相反，这些实例对内容进行操作之前创建的缓冲区的副本。 此外，`CStringT`使用锁定的缓冲区的实例不会尝试共享的任何其他缓冲区`CStringT`分配给它的实例。 在这种情况下，`CStringT`实例将另一个字符串复制到锁定缓冲区。  
  
     分配时`CStringData`结构，你必须将此字段设置以反映所允许的缓冲区的共享类型。 对于大多数实施方案，此值设置为一个。 这样的常用的写入时复制共享行为。 但是，如果字符串管理器不支持共享的字符串缓冲区，将此字段设置为锁定状态。 这将强制`CStringT`仅的实例中使用此缓冲区`CStringT`的分配。  
  
## <a name="see-also"></a>请参阅  
 [使用 CStringT 进行内存管理](../atl-mfc-shared/memory-management-with-cstringt.md)


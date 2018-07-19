---
title: 实现的自定义字符串管理器 （高级方法） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d72ce586c7c93f6bd5ade613ab2807398a13ab7
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882151"
---
# <a name="implementation-of-a-custom-string-manager-advanced-method"></a>实现的自定义字符串管理器 （高级方法）
在专用的情况下，你可能想要实现自定义字符串管理器的多个只需更改使用的堆分配内存。 在这种情况下，您必须手动实现[IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md)作为自定义字符串管理器的接口。  
  
 若要执行此操作，务必先了解如何[CStringT](../atl-mfc-shared/reference/cstringt-class.md)使用该接口来管理其字符串数据。 每个实例`CStringT`具有一个指向[CStringData](../atl-mfc-shared/reference/cstringdata-class.md)结构。 此变量长度结构包含重要信息字符串 （如长度），以及字符串的实际字符数据。 每个自定义字符串管理器负责分配和释放的请求这些结构`CStringT`。  
  
 `CStringData`结构包含四个字段：  
  
-   [pStringMgr](../atl-mfc-shared/reference/cstringdata-class.md#pstringmgr)此字段将指向`IAtlStringMgr`接口用于管理此字符串数据。 当`CStringT`需要重新分配或释放它调用的重新分配或可用方法的此接口，传递的字符串缓冲区`CStringData`结构作为参数。 分配时`CStringData`结构中字符串管理器中，必须设置此字段以指向自定义字符串管理器。  
  
-   [nDataLength](../atl-mfc-shared/reference/cstringdata-class.md#ndatalength)此字段包含不包括终止 null 的缓冲区中存储的字符串的当前逻辑长度。 `CStringT` 字符串的长度发生更改时，请更新此字段。 分配时`CStringData`结构，字符串管理器必须将此字段设置为零。 重新分配时`CStringData`结构，自定义字符串管理器必须将此字段保留不变。  
  
-   [nAllocLength](../atl-mfc-shared/reference/cstringdata-class.md#nalloclength)此字段包含的最大 （不包括终止 null），而无需重新分配它可以存储在此字符串缓冲区的字符数。 每当`CStringT`需要增加逻辑长度的字符串，它会首先检查此字段以确保在缓冲区中没有足够的空间。 如果检查失败，`CStringT`调入自定义字符串管理器重新分配缓冲区。 当分配或重新分配`CStringData`结构，必须将其设置字段到至少请求中的字符数*nChars*参数[IAtlStringMgr::Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#allocate)或[IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate)。 如果不是请求的缓冲区中没有更多的空间，可以设置此值以反映实际可用空间量。 这允许`CStringT`增长以填充整个字符串分配的空间之前将回调到要重新分配缓冲区的字符串管理器。  
  
-   [nRefs](../atl-mfc-shared/reference/cstringdata-class.md#nrefs)此字段包含字符串缓冲区的当前引用计数。 如果值为一个，接着的单个实例`CStringT`使用的缓冲区。 此外，该实例被允许读取和修改缓冲区的内容。 如果值为大于 1 的多个实例`CStringT`可以使用缓冲区。 由于共享的字符缓冲区，`CStringT`实例只能读取缓冲区的内容。 若要修改的内容，`CStringT`首次建立缓冲区的副本。 如果值为负，只有一个实例`CStringT`使用的缓冲区。 在这种情况下，缓冲区被视为锁定。 当`CStringT`实例使用锁定的缓冲区的任何其他实例`CStringT`可能会共享缓冲区。 相反，这些实例操作内容之前创建的缓冲区的副本。 此外，`CStringT`使用锁定的缓冲区的实例不会尝试共享的任何其他缓冲区`CStringT`分配给它的实例。 在这种情况下，`CStringT`实例将另一个字符串复制到锁定缓冲区。  
  
     分配时`CStringData`结构，必须设置此字段以反映可用于缓冲区进行共享的类型。 对于大多数实现，此值设置为一个。 这样的常见的写入时复制共享行为。 但是，如果字符串管理器不支持共享字符串缓冲区，将此字段设置为锁定状态。 这会强制`CStringT`仅使用实例的此缓冲区`CStringT`，分配给它。  
  
## <a name="see-also"></a>请参阅  
 [使用 CStringT 进行内存管理](../atl-mfc-shared/memory-management-with-cstringt.md)


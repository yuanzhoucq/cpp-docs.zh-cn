---
title: CFixedStringT： 示例的自定义字符串 Manager |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CFixedStringT class, using a custom string manager
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f841124fd12497fdb4dd4b813de2d803e43ff60b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359544"
---
# <a name="cfixedstringt-example-of-a-custom-string-manager"></a>CFixedStringT： 示例的自定义字符串管理器
ATL 库实现的类所使用的自定义字符串管理器的一个示例[CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md)、 调用**那么 CFixedStringMgr**。 `CFixedStringT` 派生自[CStringT](../atl-mfc-shared/reference/cstringt-class.md)并实现的一部分分配其字符数据字符串`CFixedStringT`对象本身，只要字符串是否小于指定的长度比**t_nChars**模板参数的`CFixedStringT`。 使用此方法，该字符串不需要，堆，除非字符串的长度超过固定的缓冲区的大小。 因为`CFixedStringT`并非总是不使用堆分配其字符串数据，它不能使用**CAtlStringMgr**作为其字符串经理。 它使用自定义字符串管理器 (**那么 CFixedStringMgr**)、 实现[IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md)接口。 此接口已在[实现的自定义字符串管理器 （高级方法）](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)。  
  
 构造函数**那么 CFixedStringMgr**采用三个参数：  
  
-   **pData:** 指向固定的`CStringData`要使用的结构。  
  
-   **nChars:** 最大字符数`CStringData`结构可以容纳。  
  
-   **pMgr:** 指向的指针`IAtlStringMgr`接口的"备份字符串 manager"。  
  
 构造函数存储的值`pData`和**pMgr**在其各自的成员变量 (`m_pData`和**m_pMgr**)。 然后，它设置为零，可用长度等于最大大小固定的缓冲区，以及为-1 的引用计数的缓冲区的长度。 引用计数值指示锁定缓冲区和要使用的此实例**那么 CFixedStringMgr**作为字符串经理。  
  
 将缓冲区标记为锁定可以防止其他`CStringT`中保持到缓冲区的共享的引用的实例。 如果其他`CStringT`允许实例共享就包含缓冲区的缓冲区`CFixedStringT`其他字符串仍已使用缓冲区时要删除。  
  
 **那么 CFixedStringMgr**是完整的实现`IAtlStringMgr`接口。 分别讨论了每个方法的实现。  
  
## <a name="implementation-of-cfixedstringmgrallocate"></a>CFixedStringMgr::Allocate 的实现  
 实现**CFixedStringMgr::Allocate**首先检查字符串的请求的大小是否小于或等于固定的缓冲区的大小 (存储在`m_pData`成员)。 固定的缓冲区是否足够大，**那么 CFixedStringMgr**锁定固定的缓冲区长度为零。 只要增长的字符串长度不固定的缓冲区的大小超出`CStringT`不必重新分配缓冲区。  
  
 如果字符串的请求的大小大于固定的缓冲区**那么 CFixedStringMgr**将请求转发到的备份字符串管理器。 备份字符串 manager 假定用于分配的堆中的缓冲区。 但是，在返回此缓冲区之前**那么 CFixedStringMgr**锁定缓冲区并将使用的指针替换缓冲区的字符串 manager 指针**那么 CFixedStringMgr**对象。 这可确保，尝试重新分配或释放由缓冲区`CStringT`将调入**那么 CFixedStringMgr**。  
  
## <a name="implementation-of-cfixedstringmgrreallocate"></a>CFixedStringMgr::ReAllocate 的实现  
 实现**CFixedStringMgr::ReAllocate**非常类似于其实现**分配**。  
  
 如果正在进行重新分配的缓冲区是固定的缓冲区，并且请求的缓冲区大小小于固定的缓冲区，不分配是执行的。 但是，如果正在进行重新分配的缓冲区不是固定的缓冲区，它必须与备份管理器分配的缓冲区。 在这种情况下备份管理器用于重新分配缓冲区。  
  
 如果正在进行重新分配的缓冲区是固定的缓冲区，并且新的缓冲区大小太大，以适合固定的缓冲区，**那么 CFixedStringMgr**分配一个新的缓冲区，使用的备份管理器。 固定的缓冲区的内容然后复制到新的缓冲区中。  
  
## <a name="implementation-of-cfixedstringmgrfree"></a>CFixedStringMgr::Free 的实现  
 实现**CFixedStringMgr::Free**遵循同一模式，为**分配**和`ReAllocate`。 如果正在释放缓冲区已固定的缓冲区，该方法会将其设置为零长度锁定缓冲区。 如果正在释放缓冲区已分配与备份管理器，**那么 CFixedStringMgr**使用备份管理器来释放它。  
  
## <a name="implementation-of-cfixedstringmgrclone"></a>CFixedStringMgr::Clone 的实现  
 实现**CFixedStringMgr::Clone**始终将指针返回到的备份管理器而不是**那么 CFixedStringMgr**本身。 这是因为每个实例的**那么 CFixedStringMgr**仅可使用的单个实例相关联`CStringT`。 任何其他实例`CStringT`尝试克隆 manager 应改为获取的备份管理器。 这是因为备份管理器支持与他方共享。  
  
## <a name="implementation-of-cfixedstringmgrgetnilstring"></a>CFixedStringMgr::GetNilString 的实现  
 实现**CFixedStringMgr::GetNilString**返回固定的缓冲区。 由于一对一的对应关系的**那么 CFixedStringMgr**和`CStringT`的给定的实例`CStringT`永远不会一次使用多个缓冲区。 因此，nil 字符串和真实的字符串缓冲区从不需要在同一时间。  
  
 不使用固定的缓冲区时**那么 CFixedStringMgr**可确保它进行初始化长度为零。 这使它可以用作零的字符串。 另一个好处，`nAllocLength`固定的缓冲区的成员始终设置为固定的缓冲区的完整大小。 这意味着，`CStringT`可以增长情况下调用字符串[IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate)，即使零的字符串。  
  
## <a name="requirements"></a>要求  
 **标头：** cstringt.h  
  
## <a name="see-also"></a>请参阅  
 [使用 CStringT 进行内存管理](../atl-mfc-shared/memory-management-with-cstringt.md)


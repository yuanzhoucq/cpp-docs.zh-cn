---
title: CFixedStringT:示例中的自定义字符串管理器
ms.date: 11/04/2016
helpviewer_keywords:
- CFixedStringT class, using a custom string manager
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
ms.openlocfilehash: 2b6da5d4166b220ef63500d0154ab32dc72b40f4
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740702"
---
# <a name="cfixedstringt-example-of-a-custom-string-manager"></a>CFixedStringT:示例中的自定义字符串管理器

ATL 库实现的类使用的自定义字符串管理器的一个示例[CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md)称为**那么 CFixedStringMgr**。 `CFixedStringT` 派生自[CStringT](../atl-mfc-shared/reference/cstringt-class.md)并实现一个字符串，其字符数据分配作为的一部分`CFixedStringT`对象本身，只要该字符串是指定的长度小于`t_nChars`的模板参数`CFixedStringT`. 使用此方法，该字符串不需要在堆，除非字符串的长度大小固定的缓冲区的大小超过指定值。 因为`CFixedStringT`并非总是不使用堆分配其字符串数据，它不能使用`CAtlStringMgr`为其字符串管理器。 它使用自定义字符串管理器 (`CFixedStringMgr`)，实现[IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md)接口。 中介绍了此接口[实现的自定义字符串管理器 （高级方法）](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)。

构造函数`CFixedStringMgr`采用三个参数：

- *pData:* 一个指向固定的`CStringData`要使用的结构。

- *nChars:* 最大字符数`CStringData`结构可以容纳。

- *pMgr:* 一个指向`IAtlStringMgr`接口的"备份字符串 manager"。

构造函数存储的值*pData*并*pMgr*在其各自的成员变量 (`m_pData`和`m_pMgr`)。 然后，它设置为零，可用长度等于最大大小固定的缓冲区和引用计数为-1 的缓冲区的长度。 引用计数值指示缓冲区被锁定，并使用此实例的`CFixedStringMgr`作为字符串管理器。

将缓冲区标记为锁定可以防止其他`CStringT`中保存到缓冲区的共享的引用的实例。 如果其他`CStringT`实例已允许共享可以只为所包含的缓冲区的缓冲区`CFixedStringT`以时仍在缓冲区已使用其他字符串中删除。

`CFixedStringMgr` 是完整的实现`IAtlStringMgr`接口。 分别讨论了每个方法的实现。

## <a name="implementation-of-cfixedstringmgrallocate"></a>CFixedStringMgr::Allocate 的实现

实现`CFixedStringMgr::Allocate`首先检查以查看字符串的请求的大小是否小于或等于固定缓冲区的大小 (存储在`m_pData`成员)。 如果固定的缓冲区不够大，`CFixedStringMgr`锁定固定的缓冲区长度为零。 只要增长的字符串长度不固定的缓冲区的大小超出`CStringT`将无需重新分配缓冲区。

如果字符串的请求的大小大于固定缓冲区`CFixedStringMgr`将请求转发到备份字符串管理器。 假定备份字符串管理器分配的堆中缓冲区。 但是，然后再返回此缓冲区`CFixedStringMgr`锁定缓冲区并将替换指向缓冲区的字符串管理器指针`CFixedStringMgr`对象。 这可确保可用于重新分配或释放的缓冲区`CStringT`会调用到`CFixedStringMgr`。

## <a name="implementation-of-cfixedstringmgrreallocate"></a>CFixedStringMgr::ReAllocate 的实现

实现`CFixedStringMgr::ReAllocate`非常类似于其实现`Allocate`。

如果正在进行重新分配的缓冲区是固定的缓冲区和请求的缓冲区大小小于固定缓冲区，不进行任何分配。 但是，如果正在进行重新分配的缓冲区不是固定的缓冲区，它必须与备份管理器分配的缓冲区。 在这种情况下备份管理器用于重新分配缓冲区。

如果正在进行重新分配的缓冲区是固定的缓冲区，并且新的缓冲区大小太大，无法固定缓冲区中`CFixedStringMgr`分配新的缓冲区使用的备份管理器。 然后，固定的缓冲区的内容被复制到新的缓冲区。

## <a name="implementation-of-cfixedstringmgrfree"></a>CFixedStringMgr::Free 的实现

实现`CFixedStringMgr::Free`遵循相同的模式`Allocate`和`ReAllocate`。 如果正在释放缓冲区已固定的缓冲区，该方法将其设置为零长度的锁定缓冲区。 如果正在释放缓冲区已分配与备份管理器，`CFixedStringMgr`使用备份管理器来释放它。

## <a name="implementation-of-cfixedstringmgrclone"></a>CFixedStringMgr::Clone 的实现

实现`CFixedStringMgr::Clone`始终返回一个指向备份管理器而不是`CFixedStringMgr`本身。 这是因为的每个实例`CFixedStringMgr`仅可使用的单个实例相关联`CStringT`。 任何其他实例`CStringT`尝试克隆该管理器应改为获取的备份管理器。 这是因为备份管理器支持共享。

## <a name="implementation-of-cfixedstringmgrgetnilstring"></a>CFixedStringMgr::GetNilString 的实现

实现`CFixedStringMgr::GetNilString`返回固定的缓冲区。 由于的一对一对应关系`CFixedStringMgr`并`CStringT`，给定的实例的`CStringT`永远不会一次使用多个缓冲区。 因此，空字符串和真实的字符串缓冲区从不需要在同一时间。

固定的缓冲区未被使用，只要`CFixedStringMgr`可确保使用长度为零初始化。 这使得它可以作为空字符串。 作为额外奖励，`nAllocLength`固定缓冲区的成员始终设置为固定的缓冲区的完整大小。 这意味着`CStringT`可以增长而无需调用字符串[IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate)，即使为零的字符串。

## <a name="requirements"></a>要求

**标头：** cstringt.h

## <a name="see-also"></a>请参阅

[使用 CStringT 进行内存管理](../atl-mfc-shared/memory-management-with-cstringt.md)

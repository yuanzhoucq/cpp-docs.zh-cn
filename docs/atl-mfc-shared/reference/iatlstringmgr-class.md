---
title: IAtlStringMgr 类
ms.date: 10/18/2018
f1_keywords:
- IAtlStringMgr
- ATLSIMPSTR/ATL::IAtlStringMgr
- ATLSIMPSTR/ATL::Allocate
- ATLSIMPSTR/ATL::Clone
- ATLSIMPSTR/ATL::Free
- ATLSIMPSTR/ATL::GetNilString
- ATLSIMPSTR/ATL::Reallocate
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
ms.openlocfilehash: bee9c3d27ea05a40d6835d69079fc3e0a56efb86
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219048"
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr 类

此类表示 `CStringT` 内存管理器的接口。

## <a name="syntax"></a>语法

```
__interface IAtlStringMgr
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[分配](#allocate)|调用此方法可分配新的字符串数据结构。|
|[克隆](#clone)|调用此方法以返回指向新字符串管理器的指针，以便与另一个实例一起使用 `CSimpleStringT` 。|
|[免费](#free)|调用此方法可释放字符串数据结构。|
|[GetNilString](#getnilstring)|返回一个指针，该指针指向 `CStringData` 空字符串对象使用的对象。|
|[给](#reallocate)|调用此方法可重新分配字符串数据结构。|

## <a name="remarks"></a>备注

此接口管理与 MFC 无关的字符串类使用的内存;例如[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)、 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)和[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)。

你还可以使用此类来实现自定义字符串类的自定义内存管理器。 有关详细信息，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="requirements"></a>要求

**标头：** atlsimpstr

## <a name="iatlstringmgrallocate"></a><a name="allocate"></a>IAtlStringMgr：： Allocate

分配一个新的字符串数据结构。

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>参数

*nAllocLength*<br/>
新内存块中的字符数。

*nCharSize*<br/>
字符串管理器使用的字符类型的大小（以字节为单位）。

### <a name="return-value"></a>返回值

将指针返回到新分配的内存块。

> [!NOTE]
> 不要通过引发异常来指示失败的分配。 相反，应通过返回 NULL 来发出失败的分配信号。

### <a name="remarks"></a>备注

调用[IAtlStringMgr：： Free](#free)或[IAtlStringMgr：：重新分配](#reallocate)以释放此方法分配的内存。

> [!NOTE]
> 有关用法示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrclone"></a><a name="clone"></a>IAtlStringMgr：： Clone

返回一个指针，该指针指向与另一个实例一起使用的新字符串管理器 `CSimpleStringT` 。

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>返回值

返回 `IAtlStringMgr` 对象的副本。

### <a name="remarks"></a>备注

对于新字符串需要字符串管理器时，框架通常会调用。 在大多数情况下，将 **`this`** 返回指针。

但是，如果内存管理器不支持的多个实例使用，则 `CSimpleStringT` 应返回指向共享字符串管理器的指针。

> [!NOTE]
> 有关用法示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrfree"></a><a name="free"></a>IAtlStringMgr：： Free

释放字符串数据结构。

```cpp
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>参数

*pData*<br/>
指向要释放的内存块的指针。

### <a name="remarks"></a>备注

释放之前[分配或重新分配的指定](#allocate)内存块[。](../../atl/reference/iatlmemmgr-class.md#reallocate)

> [!NOTE]
> 有关用法示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrgetnilstring"></a><a name="getnilstring"></a>IAtlStringMgr::GetNilString

返回一个指向空字符串的字符串数据结构的指针。

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>返回值

一个指针，指向 `CStringData` 用于表示空字符串的对象。

### <a name="remarks"></a>备注

调用此函数可返回空字符串的表示形式。

> [!NOTE]
> 实现自定义字符串管理器时，此函数永远不会失败。 可以通过 `CNilStringData` 在字符串管理器类中嵌入实例来确保这一点，并返回指向该实例的指针。

> [!NOTE]
> 有关用法示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrreallocate"></a><a name="reallocate"></a>IAtlStringMgr：：重新分配

重新分配字符串数据结构。

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>参数

*pData*<br/>
指向此内存管理器以前分配的内存的指针。

*nAllocLength*<br/>
新内存块中的字符数。

*nCharSize*<br/>
字符串管理器使用的字符类型的大小（以字节为单位）。

### <a name="return-value"></a>返回值

将指针返回到新分配内存块的起始位置。

### <a name="remarks"></a>备注

调用此函数可调整*pData*指定的现有内存块的大小。

调用[IAtlStringMgr：： free](#free)可释放由此方法分配的内存。

> [!NOTE]
> 有关用法示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)

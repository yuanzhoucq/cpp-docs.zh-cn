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
ms.openlocfilehash: c3fabb7a7a6da4129787d219bd83b2a35fa0c4dd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746605"
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr 类

此类表示内存管理器的`CStringT`接口。

## <a name="syntax"></a>语法

```
__interface IAtlStringMgr
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[分配](#allocate)|调用此方法以分配新的字符串数据结构。|
|[克隆](#clone)|调用此方法返回指向新字符串管理器的指针，以便与 的另一个实例一`CSimpleStringT`起使用 。|
|[免费](#free)|调用此方法以释放字符串数据结构。|
|[获得尼尔斯特林](#getnilstring)|返回指向空字符串`CStringData`对象使用的对象的指针。|
|[重新分配](#reallocate)|调用此方法以重新分配字符串数据结构。|

## <a name="remarks"></a>备注

此接口管理独立于 MFC 的字符串类使用的内存;如[CSimpleStringT、CStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)和[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)。

您还可以使用此类实现自定义字符串类的自定义内存管理器。 有关详细信息，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="requirements"></a>要求

**标题：** atlsimpstr.h

## <a name="iatlstringmgrallocate"></a><a name="allocate"></a>IAtlStringMgr：：分配

分配新的字符串数据结构。

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>参数

*nAlloc 长度*<br/>
新内存块中的字符数。

*n字符*<br/>
字符串管理器使用的字符类型的大小（以字节为单位）。

### <a name="return-value"></a>返回值

将指针返回到新分配的内存块。

> [!NOTE]
> 不要通过引发异常来发出分配失败的信号。 相反，应返回 NULL 来发出失败分配的信号。

### <a name="remarks"></a>备注

调用[IAtlStringMgr：免费](#free)或[IAtlStringMgr：重新分配](#reallocate)以释放此方法分配的内存。

> [!NOTE]
> 有关使用示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrclone"></a><a name="clone"></a>IAtlStringMgr：克隆

返回指向新字符串管理器的指针，以便与 的另一个`CSimpleStringT`实例一起使用 。

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>返回值

返回 `IAtlStringMgr` 对象的副本。

### <a name="remarks"></a>备注

当新字符串需要字符串管理器时，框架通常调用。 在大多数情况下，**将返回此**指针。

但是，如果内存管理器不支持由 的`CSimpleStringT`多个实例使用，则应返回指向可共享字符串管理器的指针。

> [!NOTE]
> 有关使用示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrfree"></a><a name="free"></a>IAtlStringMgr：免费

释放字符串数据结构。

```cpp
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>参数

*pData*<br/>
指向要释放的内存块的指针。

### <a name="remarks"></a>备注

释放以前由[分配](#allocate)或[重新分配](../../atl/reference/iatlmemmgr-class.md#reallocate)分配的指定内存块。

> [!NOTE]
> 有关使用示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrgetnilstring"></a><a name="getnilstring"></a>IAtlStringMgr：：GetNilString

返回指向空字符串的字符串数据结构的指针。

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>返回值

指向用于表示空`CStringData`字符串的对象的指针。

### <a name="remarks"></a>备注

调用此函数以返回空字符串的表示形式。

> [!NOTE]
> 实现自定义字符串管理器时，此函数绝不能失败。 可以通过在字符串管理器类中嵌入 的`CNilStringData`实例来确保这一点，并返回指向该实例的指针。

> [!NOTE]
> 有关使用示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrreallocate"></a><a name="reallocate"></a>IAtlStringMgr：重新分配

重新分配字符串数据结构。

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>参数

*pData*<br/>
指向以前由此内存管理器分配的内存的指针。

*nAlloc 长度*<br/>
新内存块中的字符数。

*n字符*<br/>
字符串管理器使用的字符类型的大小（以字节为单位）。

### <a name="return-value"></a>返回值

将指针返回到新分配内存块的起始位置。

### <a name="remarks"></a>备注

调用此函数以调整*pData*指定的现有内存块的大小。

调用[IAtlStringMgr：可自由](#free)释放此方法分配的内存。

> [!NOTE]
> 有关使用示例，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)

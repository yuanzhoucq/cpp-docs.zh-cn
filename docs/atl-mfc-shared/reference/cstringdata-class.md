---
title: CStringData 类
ms.date: 11/04/2016
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
ms.openlocfilehash: 5915d9e25588e4e35538619662281ceaf1b35ff7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317600"
---
# <a name="cstringdata-class"></a>CStringData 类

此类表示字符串对象的数据。

## <a name="syntax"></a>语法

```
struct CStringData
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[AddRef](#addref)|增加字符串数据对象的引用计数。|
|[数据](#data)|检索字符串对象的字符数据。|
|[IsLocked](#islocked)|确定关联的字符串对象的缓冲区是否锁定。|
|[IsShared](#isshared)|确定关联的字符串对象的缓冲区当前是否共享。|
|[Lock](#lock)|锁定关联的字符串对象的缓冲区。|
|[发布](#release)|释放指定的字符串对象。|
|[解 锁](#unlock)|解锁关联的字符串对象的缓冲区。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[nAlloc 长度](#nalloclength)|s 中`XCHAR`分配的数据的长度（不包括终止 null）|
|[n数据长度](#ndatalength)|s 中`XCHAR`当前使用的数据的长度（不包括终止 null）|
|[nRefs](#nrefs)|对象的当前引用计数。|
|[普斯特林姆格](#pstringmgr)|指向此字符串对象的字符串管理器的指针。|

## <a name="remarks"></a>备注

此类只能由实现自定义字符串管理器的开发人员使用。 有关自定义字符串管理器的详细信息，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)

此类封装了与较高字符串对象（如[CStringT、CSimpleStringT](../../atl-mfc-shared/reference/cstringt-class.md)或[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)对象）关联的各种类型的信息和数据。 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md) 每个较高的字符串对象都包含指向其关联`CStringData`对象的指针，允许多个字符串对象指向同一字符串数据对象。 此关系由`nRefs``CStringData`对象的引用计数 （ ） 表示。

> [!NOTE]
> 在某些情况下，字符串类型（如`CFixedString`） 不会与多个较高字符串对象共享字符串数据对象。 有关此的详细信息，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

此数据由：

- 字符串的内存管理器[（IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)类型）。

- 字符串的当前长度 （ [nData 长度](#ndatalength)） 。

- 字符串的分配长度 （ [nAlloc 长度](#nalloclength)） 。 出于性能原因，这可能与当前字符串长度不同

- `CStringData`对象的当前引用计数 （ [nRefs](#nrefs)） . 此值用于确定共享同一`CStringData`对象的字符串对象数。

- 字符串的实际字符缓冲区 （[数据](#data)） .

   > [!NOTE]
   > 字符串对象的实际字符缓冲区由字符串管理器分配并追加到该对象。 `CStringData`

## <a name="requirements"></a>要求

**标题：** atlsimpstr.h

## <a name="cstringdataaddref"></a><a name="addref"></a>弦数据：：添加参考

增加字符串对象的引用计数。

```
void AddRef() throw();
```

### <a name="remarks"></a>备注

增加字符串对象的引用计数。

> [!NOTE]
> 不要在具有负引用计数的字符串上调用此方法，因为负计数表示字符串缓冲区已锁定。

## <a name="cstringdatadata"></a><a name="data"></a>弦乐数据：:d

返回指向字符串对象字符缓冲区的指针。

```
void* data() throw();
```

### <a name="return-value"></a>返回值

指向字符串对象的字符缓冲区的指针。

### <a name="remarks"></a>备注

调用此函数以返回关联字符串对象的当前字符缓冲区。

> [!NOTE]
> 此缓冲区不是由对象分配，`CStringData`而是由字符串管理器在需要时分配。 分配时，缓冲区将追加到字符串数据对象。

## <a name="cstringdataislocked"></a><a name="islocked"></a>CStringData：：锁定

确定字符缓冲区是否锁定。

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>返回值

如果缓冲区已锁定，则返回 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

调用此函数以确定字符串对象的字符缓冲区当前是否锁定。

## <a name="cstringdataisshared"></a><a name="isshared"></a>CStringData：：共享

确定字符缓冲区是否共享。

```
bool IsShared() const throw();
```

### <a name="return-value"></a>返回值

如果缓冲区是共享的，则返回 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

调用此函数以确定字符串数据对象的字符缓冲区当前是否在多个字符串对象之间共享。

## <a name="cstringdatalock"></a><a name="lock"></a>弦数据：锁定

锁定关联字符串对象的字符缓冲区。

```
void Lock() throw();
```

### <a name="remarks"></a>备注

调用此函数以锁定字符串数据对象的字符缓冲区。 当开发人员需要直接访问字符缓冲区时，将使用锁定和解锁。 锁定的一个好示例通过`CSimpleStringT`的[LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[解锁缓冲区](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)方法演示。

> [!NOTE]
> 仅当缓冲区未在较高的字符串对象之间共享时，才能锁定字符缓冲区。

## <a name="cstringdatanalloclength"></a><a name="nalloclength"></a>CStringData：：nAlloc长度

已分配的字符缓冲区的长度。

```
int nAllocLength;
```

### <a name="remarks"></a>备注

将分配的数据缓冲区的长度存储在 s`XCHAR`中（不包括终止 null）。

## <a name="cstringdatandatalength"></a><a name="ndatalength"></a>CStringData：n数据长度

字符串对象的当前长度。

```
int nDataLength;
```

### <a name="remarks"></a>备注

将当前使用的数据的长度存储在 s`XCHAR`中（不包括终止 null）。

## <a name="cstringdatanrefs"></a><a name="nrefs"></a>CStringData：：nRefs

字符串数据对象的引用计数。

```
long nRefs;
```

### <a name="remarks"></a>备注

存储字符串数据对象的引用计数。 此计数指示与字符串数据对象关联的较高字符串对象的数量。 负值表示字符串数据对象当前已锁定。

## <a name="cstringdatapstringmgr"></a><a name="pstringmgr"></a>弦乐数据：:pStringMgr

关联的字符串对象的内存管理器。

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>备注

存储关联字符串对象的内存管理器。 有关内存管理器和字符串的详细信息，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="cstringdatarelease"></a><a name="release"></a>CStringData：：发布

取消字符串数据对象的引用计数。

```
void Release() throw();
```

### <a name="remarks"></a>备注

调用此函数以递减引用计数，在引用计数达到零`CStringData`时释放结构。 这通常在删除字符串对象时完成，因此不再需要引用字符串数据对象。

例如，以下代码将调用`CStringData::Release`与 关联的`str1`字符串数据对象。

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

## <a name="cstringdataunlock"></a><a name="unlock"></a>CStringData：：解锁

解锁关联的字符串对象的字符缓冲区。

```
void Unlock() throw();
```

### <a name="remarks"></a>备注

调用此函数以解锁字符串数据对象的字符缓冲区。 一旦缓冲区解锁，它是可共享的，可以进行引用计数。

> [!NOTE]
> 每个`Lock`调用都必须与 相应的调用`Unlock`匹配。

当开发人员必须确保字符串数据不共享时，将使用锁定和解锁。 锁定的一个好示例通过`CSimpleStringT`的[LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[解锁缓冲区](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)方法演示。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)

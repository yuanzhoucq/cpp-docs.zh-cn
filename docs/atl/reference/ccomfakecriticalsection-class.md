---
title: CComFakeCriticalSection 类
ms.date: 11/04/2016
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
helpviewer_keywords:
- CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
ms.openlocfilehash: cf2408afb70dd6e2be27e22605f46b51b75ad602
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519377"
---
# <a name="ccomfakecriticalsection-class"></a>CComFakeCriticalSection 类

此类提供了将相同的方法作为[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) ，但不提供关键部分。

## <a name="syntax"></a>语法

```
class CComFakeCriticalSection
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComFakeCriticalSection::Init](#init)|任何影响，因为没有关键部分。|
|[CComFakeCriticalSection::Lock](#lock)|任何影响，因为没有关键部分。|
|[CComFakeCriticalSection::Term](#term)|任何影响，因为没有关键部分。|
|[CComFakeCriticalSection::Unlock](#unlock)|任何影响，因为没有关键部分。|

## <a name="remarks"></a>备注

`CComFakeCriticalSection` 镜像中找到的方法[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。 但是，`CComFakeCriticalSection`不提供关键部分; 因此，其方法不执行任何操作。

通常情况下，使用`CComFakeCriticalSection`通过`typedef`名称，或者`AutoCriticalSection`或`CriticalSection`。 使用时[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，这两种`typedef`名称引用`CComFakeCriticalSection`。 使用时[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)，它们引用[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)和`CComCriticalSection`分别。

## <a name="requirements"></a>要求

**标头：** atlcore.h

##  <a name="init"></a>  CComFakeCriticalSection::Init

任何影响，因为没有关键部分。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>返回值

返回 S_OK。

##  <a name="lock"></a>  CComFakeCriticalSection::Lock

任何影响，因为没有关键部分。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>返回值

返回 S_OK。

##  <a name="term"></a>  CComFakeCriticalSection::Term

任何影响，因为没有关键部分。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>返回值

返回 S_OK。

##  <a name="unlock"></a>  CComFakeCriticalSection::Unlock

任何影响，因为没有关键部分。

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>返回值

返回 S_OK。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)

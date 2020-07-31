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
ms.openlocfilehash: 5ada0fbed705af34391709653dbd3638fed32bf7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226576"
---
# <a name="ccomfakecriticalsection-class"></a>CComFakeCriticalSection 类

此类提供与[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)相同的方法，但不提供临界区。

## <a name="syntax"></a>语法

```
class CComFakeCriticalSection
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CComFakeCriticalSection：： Init](#init)|不执行任何操作，因为没有关键部分。|
|[CComFakeCriticalSection：： Lock](#lock)|不执行任何操作，因为没有关键部分。|
|[CComFakeCriticalSection：： Term](#term)|不执行任何操作，因为没有关键部分。|
|[CComFakeCriticalSection：： Unlock](#unlock)|不执行任何操作，因为没有关键部分。|

## <a name="remarks"></a>备注

`CComFakeCriticalSection`镜像[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)中的方法。 但是， `CComFakeCriticalSection` 并不提供临界区，因此它的方法不执行任何操作。

通常，可以 `CComFakeCriticalSection` 通过名称使用 **`typedef`** `AutoCriticalSection` 或 `CriticalSection` 。 使用[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)时，这两个 **`typedef`** 名称引用 `CComFakeCriticalSection` 。 当使用[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)时，它们分别引用[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)和 `CComCriticalSection` 。

## <a name="requirements"></a>要求

**标头：** atlcore

## <a name="ccomfakecriticalsectioninit"></a><a name="init"></a>CComFakeCriticalSection：： Init

不执行任何操作，因为没有关键部分。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>返回值

返回 S_OK。

## <a name="ccomfakecriticalsectionlock"></a><a name="lock"></a>CComFakeCriticalSection：： Lock

不执行任何操作，因为没有关键部分。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>返回值

返回 S_OK。

## <a name="ccomfakecriticalsectionterm"></a><a name="term"></a>CComFakeCriticalSection：： Term

不执行任何操作，因为没有关键部分。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>返回值

返回 S_OK。

## <a name="ccomfakecriticalsectionunlock"></a><a name="unlock"></a>CComFakeCriticalSection：： Unlock

不执行任何操作，因为没有关键部分。

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>返回值

返回 S_OK。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)

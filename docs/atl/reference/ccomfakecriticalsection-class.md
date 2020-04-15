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
ms.openlocfilehash: 4a5b9ba3551397a9c3d59a343e9c6b55b1c1207e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327855"
---
# <a name="ccomfakecriticalsection-class"></a>CComFakeCriticalSection 类

此类提供的方法与[CCom临界节](../../atl/reference/ccomcriticalsection-class.md)相同，但不提供关键部分。

## <a name="syntax"></a>语法

```
class CComFakeCriticalSection
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CcomFake关键部分：：Init](#init)|由于没有关键部分，因此不执行任何操作。|
|[CComFake关键部分：：锁定](#lock)|由于没有关键部分，因此不执行任何操作。|
|[CComFake关键部分：：学期](#term)|由于没有关键部分，因此不执行任何操作。|
|[CComFake关键部分：：解锁](#unlock)|由于没有关键部分，因此不执行任何操作。|

## <a name="remarks"></a>备注

`CComFakeCriticalSection`镜像[CCom临界节](../../atl/reference/ccomcriticalsection-class.md)中找到的方法。 但是，`CComFakeCriticalSection`不提供关键部分;但是，不提供关键部分。因此，它的方法什么都不做。

通常`CComFakeCriticalSection`，您可以通过`typedef`名称或`AutoCriticalSection`。 `CriticalSection` 当使用[CCom单线程模型](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)时，这`typedef`两个名称`CComFakeCriticalSection`都引用。 当使用[CComMultiThread模型](../../atl/reference/ccommultithreadmodel-class.md)时，它们分别引用[CComAuto临界部分](../../atl/reference/ccomautocriticalsection-class.md)和`CComCriticalSection`。

## <a name="requirements"></a>要求

**标题：** atlcore.h

## <a name="ccomfakecriticalsectioninit"></a><a name="init"></a>CcomFake关键部分：：Init

由于没有关键部分，因此不执行任何操作。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>返回值

返回S_OK。

## <a name="ccomfakecriticalsectionlock"></a><a name="lock"></a>CComFake关键部分：：锁定

由于没有关键部分，因此不执行任何操作。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>返回值

返回S_OK。

## <a name="ccomfakecriticalsectionterm"></a><a name="term"></a>CComFake关键部分：：学期

由于没有关键部分，因此不执行任何操作。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>返回值

返回S_OK。

## <a name="ccomfakecriticalsectionunlock"></a><a name="unlock"></a>CComFake关键部分：：解锁

由于没有关键部分，因此不执行任何操作。

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>返回值

返回S_OK。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)

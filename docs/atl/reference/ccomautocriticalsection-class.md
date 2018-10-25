---
title: CComAutoCriticalSection 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40fa13ecf743bf8e6aa0cd75b16bec65131fe267
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061074"
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection 类

`CComAutoCriticalSection` 提供方法用于获取并释放关键节对象的所有权。

## <a name="syntax"></a>语法

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|构造函数。|
|[CComAutoCriticalSection:: ~ CComAutoCriticalSection](#dtor)|析构函数。|

## <a name="remarks"></a>备注

`CComAutoCriticalSection` 类似于类[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)，除`CComAutoCriticalSection`自动初始化的构造函数中的关键部分对象。

通常情况下，使用`CComAutoCriticalSection`通过`typedef`名称[AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection)。 此名称引用`CComAutoCriticalSection`时[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)正在使用。

`Init`并`Term`方法从[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)时使用此类不可用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>要求

**标头：** atlcore.h

##  <a name="ccomautocriticalsection"></a>  CComAutoCriticalSection::CComAutoCriticalSection

构造函数。

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>备注

调用 Win32 函数[InitializeCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsection)，其中初始化关键部分对象。

##  <a name="dtor"></a>  CComAutoCriticalSection:: ~ CComAutoCriticalSection

析构函数。

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>备注

析构函数调用[DeleteCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-deletecriticalsection)，以释放关键节对象使用的所有系统资源。

## <a name="see-also"></a>请参阅

[CComFakeCriticalSection 类](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)

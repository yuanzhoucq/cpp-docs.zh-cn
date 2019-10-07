---
title: CComAutoCriticalSection 类
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 116c550f45bf622e7620b3a6f552339b4bcc24a7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497931"
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection 类

`CComAutoCriticalSection`提供用于获取和释放关键节对象的所有权的方法。

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

`CComAutoCriticalSection`类似于类[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), 但`CComAutoCriticalSection`在构造函数中自动初始化临界区对象。

通常, 使用`CComAutoCriticalSection` `typedef`名称[AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection)。 当使用`CComAutoCriticalSection` [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)时, 此名称引用。

使用`Init`此`Term`类时, [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)中的和方法不可用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>要求

**标头:** atlcore

##  <a name="ccomautocriticalsection"></a>CComAutoCriticalSection::CComAutoCriticalSection

构造函数。

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>备注

调用 Win32 函数[InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), 该函数初始化临界区对象。

##  <a name="dtor"></a>CComAutoCriticalSection:: ~ CComAutoCriticalSection

析构函数。

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>备注

析构函数调用[DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), 后者释放由临界区对象使用的所有系统资源。

## <a name="see-also"></a>请参阅

[CComFakeCriticalSection 类](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)

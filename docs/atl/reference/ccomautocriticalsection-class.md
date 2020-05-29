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
ms.openlocfilehash: 8cbf08082fd24ef2cf0e8794e2944a799baec084
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321092"
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection 类

`CComAutoCriticalSection`提供了获取和释放关键部分对象所有权的方法。

## <a name="syntax"></a>语法

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CCom自动临界部分：cCom自动临界部分](#ccomautocriticalsection)|构造函数。|
|[CCom自动临界部分：：_CCom自动临界部分](#dtor)|析构函数。|

## <a name="remarks"></a>备注

`CComAutoCriticalSection`与类[CCom临界节](../../atl/reference/ccomcriticalsection-class.md)类似，除了`CComAutoCriticalSection`在构造函数中自动初始化关键截面对象。

通常，您可以通过`typedef`名称`CComAutoCriticalSection`["自动关键节](ccommultithreadmodel-class.md#autocriticalsection)"来使用 。 此名称引用`CComAutoCriticalSection`时，使用[CComMultiThreadModel。](../../atl/reference/ccommultithreadmodel-class.md)

使用`Init`此类`Term`时[，CCom临界节](../../atl/reference/ccomcriticalsection-class.md)中的 和 方法不可用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CCom临界部分](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>要求

**标题：** atlcore.h

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="ccomautocriticalsection"></a>CCom自动临界部分：cCom自动临界部分

构造函数。

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>备注

调用 Win32 函数[初始化关键节](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection)，它初始化关键节对象。

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="dtor"></a>CCom自动临界部分：：_CCom自动临界部分

析构函数。

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>备注

析构函数调用[Delete关键节](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection)，它释放关键节对象使用的所有系统资源。

## <a name="see-also"></a>另请参阅

[CComFakeCriticalSection 类](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)

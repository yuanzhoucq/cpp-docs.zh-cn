---
title: CAtlAutoThreadModuleT 类
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: e7b7a327d7c47c4472b43ed58fbe9ad0556a7620
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321546"
---
# <a name="catlautothreadmodulet-class"></a>CAtlAutoThreadModuleT 类

此类提供了实现线程池、单元模型 COM 服务器的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

#### <a name="parameters"></a>参数

*T*<br/>
将实现 COM 服务器的类。

*线程定位器*<br/>
管理线程选择的类。 默认值为[CcomSimpleThreadallocator](../../atl/reference/ccomsimplethreadallocator-class.md)。

*dwWait*<br/>
指定超时间隔（以毫秒为单位）。 默认值为"INFINITE"，这意味着该方法的超时间隔永远不会过去。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlAutoThreadModuleT：：获取默认线程](#getdefaultthreads)|此静态函数根据处理器数动态计算并返回 EXE 模块的最大线程数。|

## <a name="remarks"></a>备注

[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)源自`CAtlAutoThreadModuleT`，以便实现线程池、单元模型 COM 服务器。 它取代了过时的类[CComAutoThreadModule。](../../atl/reference/ccomautothreadmodule-class.md)

> [!NOTE]
> 此类不应在 DLL 中使用，因为卸载 DLL 时，INFINITE 的默认*dwWait*值将导致死锁。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a>CAtlAutoThreadModuleT：：获取默认线程

此静态函数根据处理器数动态计算并返回 EXE 模块的最大线程数。

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>返回值

要在 EXE 模块中创建的线程数。

### <a name="remarks"></a>备注

如果要使用其他方法来计算线程数，则重写此方法。 默认情况下，线程数基于处理器数。

## <a name="see-also"></a>另请参阅

[IAtlAutoThreadModule 类](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[IAtlAutoThreadModule 类](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[模块类](../../atl/atl-module-classes.md)

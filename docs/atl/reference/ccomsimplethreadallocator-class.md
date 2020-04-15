---
title: CComSimpleThreadAllocator 类
ms.date: 11/04/2016
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
ms.openlocfilehash: 4a3cce492db4db9f46aeb4efe738ee6a594ddcfc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327349"
---
# <a name="ccomsimplethreadallocator-class"></a>CComSimpleThreadAllocator 类

此类管理类`CComAutoThreadModule`的线程选择。

## <a name="syntax"></a>语法

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCom简单线程定位器：获取线程](#getthread)|选择线程。|

## <a name="remarks"></a>备注

`CComSimpleThreadAllocator`管理[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)的线程选择。 `CComSimpleThreadAllocator::GetThread`只需循环遍过每个线程，然后返回序列中的下一个线程。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccomsimplethreadallocatorgetthread"></a><a name="getthread"></a>CCom简单线程定位器：获取线程

通过指定序列中的下一个线程来选择线程。

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>参数

*pApt*<br/>
未用于 ATL 的默认实现。

*nThreads*<br/>
EXE 模块中的最大线程数。

### <a name="return-value"></a>返回值

零和 *（nThreads* - 1） 之间的整数。 标识 EXE 模块中的一个线程。

### <a name="remarks"></a>备注

您可以重写`GetThread`以提供不同的选择方法或使用*pApt*参数。

`GetThread`由[CComAutoThreadModule 调用：：创建实例](../../atl/reference/ccomautothreadmodule-class.md#createinstance)。

## <a name="see-also"></a>另请参阅

[CComApartment 类](../../atl/reference/ccomapartment-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)

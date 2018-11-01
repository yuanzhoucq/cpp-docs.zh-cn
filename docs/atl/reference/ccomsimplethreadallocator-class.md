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
ms.openlocfilehash: 1644014048b27b7ab6076783c5025140527a7ff5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637536"
---
# <a name="ccomsimplethreadallocator-class"></a>CComSimpleThreadAllocator 类

此类管理类的线程选择`CComAutoThreadModule`。

## <a name="syntax"></a>语法

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComSimpleThreadAllocator::GetThread](#getthread)|选择一个线程。|

## <a name="remarks"></a>备注

`CComSimpleThreadAllocator` 管理的线程选择[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。 `CComSimpleThreadAllocator::GetThread` 只需循环访问每个线程，并返回序列中的下一个。

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="getthread"></a>  CComSimpleThreadAllocator::GetThread

选择一个线程通过指定序列中的下一个线程。

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>参数

*pApt*<br/>
不使用 ATL 的默认实现中。

*nThreads*<br/>
最大 EXE 模块中的线程数。

### <a name="return-value"></a>返回值

一个整数，介于零和 (*nThreads* -1)。 标识一个 EXE 模块中的线程。

### <a name="remarks"></a>备注

您可以重写`GetThread`可以提供所选内容的不同方法，或使利用*pApt*参数。

`GetThread` 调用[CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance)。

## <a name="see-also"></a>请参阅

[CComApartment 类](../../atl/reference/ccomapartment-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)

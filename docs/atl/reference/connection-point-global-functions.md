---
title: 连接点全局函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f68c22ff88ac92357dabfef8076c160271a76378
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756485"
---
# <a name="connection-point-global-functions"></a>连接点全局函数

这些函数提供支持的连接点和接收器映射。

> [!IMPORTANT]
>  下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

|||
|-|-|
|[AtlAdvise](#atladvise)|在对象的连接点和客户端的接收器间创建连接。|
|[AtlUnadvise](#atlunadvise)|通过建立的连接将终止`AtlAdvise`。|
|[AtlAdviseSinkMap](#atladvisesinkmap)|建议或取消通知事件接收器映射中的条目。|  

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="atladvise"></a>  AtlAdvise

在对象的连接点和客户端的接收器间创建连接。

> [!IMPORTANT]
>  此函数不能在 Windows 运行时中执行的应用程序中使用。

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>参数

*pUnkCP*  
[in]一个指向`IUnknown`对象的客户端想要使用连接。

*pUnk*  
[in]指向客户端的`IUnknown`。

*iid*  
[in]连接点的 GUID。 通常情况下，这是与连接点管理输出接口相同。

*pdw*  
[out]一个指向唯一标识连接的 cookie。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

接收器会实现连接点所支持的输出接口。 客户端使用*pdw*要删除的连接将其传递到 cookie [AtlUnadvise](#atlunadvise)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

##  <a name="atlunadvise"></a>  AtlUnadvise

通过建立的连接将终止[AtlAdvise](#atladvise)。

> [!IMPORTANT]
>  此函数不能在 Windows 运行时中执行的应用程序中使用。

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>参数

*pUnkCP*  
[in]一个指向`IUnknown`的客户端连接使用的对象。

*iid*  
[in]连接点的 GUID。 通常情况下，这是与连接点管理输出接口相同。

*数据仓库*  
[in]唯一标识连接 cookie。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

##  <a name="atladvisesinkmap"></a>  AtlAdviseSinkMap

调用此函数可在对象的接收器事件映射中建议或不建议所有条目。

> [!IMPORTANT]
>  此函数不能在 Windows 运行时中执行的应用程序中使用。

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>参数

*pT*  
[in]指向包含接收器映射的对象的指针。

*bAdvise*  
[in]如果接收器的所有项都都可以收到通知;如果将要 unadvised 接收器的所有条目，则为 FALSE。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>请参阅

[函数](../../atl/reference/atl-functions.md)   
[连接点宏](../../atl/reference/connection-point-macros.md)

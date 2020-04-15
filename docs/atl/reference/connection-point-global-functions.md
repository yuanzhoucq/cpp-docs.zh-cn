---
title: 连接点全局函数
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
ms.openlocfilehash: 6474297f8b9adf04541f7d232fb88d5e52d4e88c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331532"
---
# <a name="connection-point-global-functions"></a>连接点全局函数

这些功能支持连接点和接收器贴图。

> [!IMPORTANT]
> 下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

|||
|-|-|
|[AtlAdvise](#atladvise)|在对象的连接点和客户端的接收器间创建连接。|
|[AtlUnadvise](#atlunadvise)|终止通过`AtlAdvise`建立的连接。|
|[AtlAdviseSinkMap](#atladvisesinkmap)|建议或不建议事件接收器地图中的条目。|

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="atladvise"></a><a name="atladvise"></a>Atl建议

在对象的连接点和客户端的接收器间创建连接。

> [!IMPORTANT]
> 此函数不能在 Windows 运行时中执行的应用程序中使用。

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>参数

*pUnkCP*<br/>
[在]指向客户端要连接`IUnknown`的对象的指针。

*朋 克*<br/>
[在]指向客户端的`IUnknown`指针。

*Iid*<br/>
[在]连接点的 GUID。 通常，这与连接点管理的传出接口相同。

*pdw*<br/>
[出]指向唯一标识连接的 Cookie 的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

接收器实现连接点支持的传出接口。 客户端使用*pdw* Cookie 将其传递给[AtlUn 建议](#atlunadvise)来删除连接。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

## <a name="atlunadvise"></a><a name="atlunadvise"></a>AtlUn建议

终止通过[AtlAdvise](#atladvise)建立的连接。

> [!IMPORTANT]
> 此函数不能在 Windows 运行时中执行的应用程序中使用。

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>参数

*pUnkCP*<br/>
[在]指向客户端所连接`IUnknown`的对象的指针。

*Iid*<br/>
[在]连接点的 GUID。 通常，这与连接点管理的传出接口相同。

*dw*<br/>
[在]唯一标识连接的 Cookie。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

## <a name="atladvisesinkmap"></a><a name="atladvisesinkmap"></a>AtlAdviseSinkMap

调用此函数可在对象的接收器事件映射中建议或不建议所有条目。

> [!IMPORTANT]
> 此函数不能在 Windows 运行时中执行的应用程序中使用。

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>参数

*铂*<br/>
[在]指向包含接收器贴图的对象的指针。

*b 建议*<br/>
[在]如果建议所有接收器条目，则为 TRUE;如果所有接收器条目均未通知，则 FALSE。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>另请参阅

[函数](../../atl/reference/atl-functions.md)<br/>
[连接点宏](../../atl/reference/connection-point-macros.md)

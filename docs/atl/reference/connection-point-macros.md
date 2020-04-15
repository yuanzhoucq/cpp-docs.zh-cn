---
title: 连接点宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: 361cf6ab2c7af142c1d57c002681ccf6e4a87bda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331499"
---
# <a name="connection-point-macros"></a>连接点宏

这些宏定义连接点映射和条目。

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|标记连接点映射条目的开头。|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|在地图中输入连接点。|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| （视觉工作室 2017）类似于CONNECTION_POINT_ENTRY但获取指向 iid 的指针。|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|标记连接点映射条目的末尾。|

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="begin_connection_point_map"></a><a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP

标记连接点映射条目的开头。

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>参数

** x <br/>
[在]包含连接点的类的名称。

### <a name="remarks"></a>备注

使用BEGIN_CONNECTION_POINT_MAP宏启动连接点映射，使用[CONNECTION_POINT_ENTRY](#connection_point_entry)宏为每个连接点添加条目，然后使用[END_CONNECTION_POINT_MAP](#end_connection_point_map)宏完成地图。

有关 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

## <a name="connection_point_entry-and-connection_point_entry_p"></a><a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY和CONNECTION_POINT_ENTRY_P

将指定接口的连接点输入到连接点映射中，以便可以访问它。

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]要添加到连接点映射的接口的 GUID。

*皮伊德*<br/>
[在]指向要添加的接口的 GUID 的指针。

### <a name="remarks"></a>备注

地图中的连接点条目由[IConnectionPoint 容器Impl 使用](../../atl/reference/iconnectionpointcontainerimpl-class.md)。 包含连接点映射的类必须从`IConnectionPointContainerImpl`继承。

使用[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)宏启动连接点映射，使用CONNECTION_POINT_ENTRY宏为每个连接点添加条目，然后使用[END_CONNECTION_POINT_MAP](#end_connection_point_map)宏完成地图。

有关 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

## <a name="end_connection_point_map"></a><a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP

标记连接点映射条目的末尾。

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>备注

使用[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)宏启动连接点映射，使用[CONNECTION_POINT_ENTRY](#connection_point_entry)宏为每个连接点添加条目，然后使用END_CONNECTION_POINT_MAP宏完成地图。

有关 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)<br/>
[连接点全局函数](../../atl/reference/connection-point-global-functions.md)

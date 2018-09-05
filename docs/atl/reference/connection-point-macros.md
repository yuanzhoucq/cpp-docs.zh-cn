---
title: 连接点宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 226c0b0d0f1fc316d5b78884a4d6e260296c52f9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752188"
---
# <a name="connection-point-macros"></a>连接点宏

这些宏定义连接点映射和条目。

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|表示连接点的映射条目的开头。|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|在映射中输入连接的点。|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017)类似于 CONNECTION_POINT_ENTRY 但采用一个指向 iid。|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|表示连接点映射项的结尾。|  

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="begin_connection_point_map"></a>  BEGIN_CONNECTION_POINT_MAP

表示连接点的映射条目的开头。

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>参数

*x*  
[in]包含连接点的类的名称。

### <a name="remarks"></a>备注

使用 BEGIN_CONNECTION_POINT_MAP 宏启动连接点映射，您使用的连接点的每个添加的条目[CONNECTION_POINT_ENTRY](#connection_point_entry)宏，并完成对地图[END_CONNECTION_POINT_MAP](#end_connection_point_map)宏。

有关在 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

##  <a name="connection_point_entry"></a>  CONNECTION_POINT_ENTRY 和 CONNECTION_POINT_ENTRY_P

为指定接口进入连接点映射到的连接点，以便对其进行访问。

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>参数

*iid*  
[in]正在添加连接点映射到的接口的 GUID。 

*piid*  
[in]指向要添加真正接口的 GUID 的指针。

### <a name="remarks"></a>备注

使用映射中的连接点条目[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)。 包含连接点映射的类必须继承`IConnectionPointContainerImpl`。

开始使用连接点映射[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)宏，将项目添加为每个连接点与 CONNECTION_POINT_ENTRY 宏保持一致，并完成与映射[END_CONNECTION_POINT_MAP](#end_connection_point_map)宏。

有关在 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

##  <a name="end_connection_point_map"></a>  END_CONNECTION_POINT_MAP

表示连接点映射项的结尾。

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>备注

开始使用连接点映射[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)宏，为每个连接点与添加条目[CONNECTION_POINT_ENTRY](#connection_point_entry)宏，并完成与 END_ 映射CONNECTION_POINT_MAP 宏。

有关在 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)   
[连接点全局函数](../../atl/reference/connection-point-global-functions.md)

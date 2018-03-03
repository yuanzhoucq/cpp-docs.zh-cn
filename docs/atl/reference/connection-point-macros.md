---
title: "连接点宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f98b5abd00f1d7ac3e3d69b0e22b549fdea35a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="connection-point-macros"></a>连接点宏
这些宏定义连接点图和条目。  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|标记的连接点的映射条目的开始。|  
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|在映射中输入连接的点。|  
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017)与 CONNECTION_POINT_ENTRY 类似但采用指向 iid 的。|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|将标记的末尾连接点的映射条目。|  

## <a name="requirements"></a>惠?  
 **标头：** atlcom.h 
   
##  <a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP  
 标记的连接点的映射条目的开始。  
  
```
BEGIN_CONNECTION_POINT_MAP(x)
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]包含的连接点的类名称。  
  
### <a name="remarks"></a>备注  
 启动与你连接点映射`BEGIN_CONNECTION_POINT_MAP`宏，为每个连接点与添加条目[CONNECTION_POINT_ENTRY](#connection_point_entry)宏，并完成对地图[END_CONNECTION_POINT_MAP](#end_connection_point_map)宏。  
  
 有关 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]  
  
##  <a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY 和 CONNECTION_POINT_ENTRY_P  
 为指定接口输入连接点映射到的连接点，以便可以进行访问。  
  
```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]添加连接点映射到接口的 GUID。 
 
 `piid`  
 [in]指向正在添加接口的 GUID 的指针。   
  
### <a name="remarks"></a>备注  
 在映射中的连接点条目由[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)。 包含连接点映射的类必须继承自`IConnectionPointContainerImpl`。  
  
 启动与你连接点映射[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)宏，为每个连接点与添加条目`CONNECTION_POINT_ENTRY`宏，并完成对地图[END_CONNECTION_POINT_MAP](#end_connection_point_map)宏。  
  
 有关 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]  
  
##  <a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP  
 将标记的末尾连接点的映射条目。  
  
```
END_CONNECTION_POINT_MAP()
```  
  
### <a name="remarks"></a>备注  
 启动与你连接点映射[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)宏，为每个连接点与添加条目[CONNECTION_POINT_ENTRY](#connection_point_entry)宏，并完成用映射`END_CONNECTION_POINT_MAP`宏。  
  
 有关 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]  
  
## <a name="see-also"></a>请参阅  
 [宏](../../atl/reference/atl-macros.md)   
 [连接点全局函数](../../atl/reference/connection-point-global-functions.md)

---
title: "连接点宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8cdedc5cfac9d49df812ae6fcfcc548201b1edb5
ms.openlocfilehash: c16b6f2f889745270a51a32a1449add86dec6ecb
ms.lasthandoff: 02/24/2017

---
# <a name="connection-point-macros"></a>连接点宏
这些宏定义连接点映射和条目。  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|标记连接点的映射条目的开始。|  
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|进入到映射中的连接点。|  
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| （visual Studio 于 2017 年）与 CONNECTION_POINT_ENTRY 类似但采用指向 iid 的指针。|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|将标记连接点的映射条目的末尾。|  

## <a name="requirements"></a>要求  
 **标头︰** atlcom.h 
   
##  <a name="a-namebeginconnectionpointmapa--beginconnectionpointmap"></a><a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP  
 标记连接点的映射条目的开始。  
  
```
BEGIN_CONNECTION_POINT_MAP(x)
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]包含的连接点的类的名称。  
  
### <a name="remarks"></a>备注  
 开始使用您连接点映射`BEGIN_CONNECTION_POINT_MAP`宏，为每个连接点与添加项[CONNECTION_POINT_ENTRY](#connection_point_entry)宏，并完成用映射[END_CONNECTION_POINT_MAP](#end_connection_point_map)宏。  
  
 关于 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&101;](../../atl/codesnippet/cpp/connection-point-macros_1.h)]  
  
##  <a name="a-nameconnectionpointentrya--connectionpointentry-and-connectionpointentryp"></a><a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY 和 CONNECTION_POINT_ENTRY_P  
 指定的接口输入连接点映射到的连接点，以便可以访问它。  
  
```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]添加连接点映射到该接口的 GUID。 
 
 `piid`  
 [in]指向要添加处理接口的 GUID 的指针。   
  
### <a name="remarks"></a>备注  
 在映射中的连接点条目由[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)。 包含连接点映射的类必须继承自`IConnectionPointContainerImpl`。  
  
 开始使用您连接点映射[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)宏，为每个连接点与添加项`CONNECTION_POINT_ENTRY`宏，并完成用映射[END_CONNECTION_POINT_MAP](#end_connection_point_map)宏。  
  
 关于 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&120;](../../atl/codesnippet/cpp/connection-point-macros_2.h)]  
  
##  <a name="a-nameendconnectionpointmapa--endconnectionpointmap"></a><a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP  
 将标记连接点的映射条目的末尾。  
  
```
END_CONNECTION_POINT_MAP()
```  
  
### <a name="remarks"></a>备注  
 开始使用您连接点映射[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)宏，为每个连接点与添加项[CONNECTION_POINT_ENTRY](#connection_point_entry)宏，并完成用映射`END_CONNECTION_POINT_MAP`宏。  
  
 关于 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&128;](../../atl/codesnippet/cpp/connection-point-macros_3.h)]  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)   
 [连接点的全局函数](../../atl/reference/connection-point-global-functions.md)


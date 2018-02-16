---
title: "IRowsetNotifyCP 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetNotifyCP
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyCP class
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7d20a4eb011b67a743e91f1f8340c80ea146bb7c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP 类
实现连接点接口的提供程序站点[IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)。  
  
## <a name="syntax"></a>语法

```cpp
template <class T, class ReentrantEventSync = CComSharedMutex>  
class IRowsetNotifyCP :   
   public IConnectionPointImpl<  
      T,   
      piid = &__uuidof(IRowsetNotify),   
      CComDynamicUnkArray DynamicUnkArray>,  
   public ReentrantEventSync  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 从派生的类`IRowsetNotifyCP`。  
  
 `ReentrantEventSync`  
 支持可重入性 mutex 类 (默认值是**CComSharedMutex**)。 互斥体是一个允许一个线程互相排斥的方式访问资源的同步对象。  
  
 `piid`  
 接口 ID 指针 (**IID\***) 为**IRowsetNotify**连接点接口。 默认值是**& __uuidof(IRowsetNotify)**。  
  
 `DynamicUnkArray`  
 类型的数组[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，这是一个动态分配的数组**IUnknown**指向客户端接收器接口。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[Fire_OnFieldChange](../../data/oledb/irowsetnotifycp-fire-onfieldchange.md)|通知对列的值的更改的使用者。|  
|[Fire_OnRowChange](../../data/oledb/irowsetnotifycp-fire-onrowchange.md)|通知更改影响的行的使用者。|  
|[Fire_OnRowsetChange](../../data/oledb/irowsetnotifycp-fire-onrowsetchange.md)|通知更改影响整个行集的使用者。|  
  
## <a name="remarks"></a>备注  
 `IRowsetNotifyCP` 实现广播函数向侦听器建议的连接点**IID_IRowsetNotify**对行集的内容的更改。  
  
 请注意，你还必须实现并注册`IRowsetNotify`使用使用者 （也称为"接收器"） 上[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)以便使用者可以处理通知。 请参阅[接收通知](../../data/oledb/receiving-notifications.md)如何实现上使用者连接点接口。  
  
 有关实现通知的详细信息，请参阅"支持通知"[创建可更新提供程序](../../data/oledb/creating-an-updatable-provider.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [通知 (COM)](http://msdn.microsoft.com/library/windows/desktop/ms678433)   
 [BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)   
 [END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)   
 [CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)   
 [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)
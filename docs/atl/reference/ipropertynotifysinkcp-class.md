---
title: IPropertyNotifySinkCP 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3fddd187dd6df58c4013b9c1fc7a08d5f644a0db
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203158"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP 类
此类公开[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)作为可连接对象上的传出接口的接口。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
## <a name="syntax"></a>语法  
  
```
template<class T, class CDV = CComDynamicUnkArray>  
class IPropertyNotifySinkCP 
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```    
  
#### <a name="parameters"></a>参数  
 *T*  
 您的类，派生自`IPropertyNotifySinkCP`。  
  
 *CDV*  
 类，用于管理连接点和其接收器之间的连接。 默认值是[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，它允许无限制的连接。 此外可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md)，它指定固定的数量的连接。  
  
## <a name="remarks"></a>备注  
 `IPropertyNotifySinkCP` 继承通过其基类，所有方法[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)。  
  
 [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)接口允许接收器对象以接收有关属性更改通知。 类`IPropertyNotifySinkCP`作为可连接对象上的传出接口公开此接口。 客户端必须实现`IPropertyNotifySink`接收器上的方法。  
  
 从类派生`IPropertyNotifySinkCP`当你想要创建的连接点的表示`IPropertyNotifySink`接口。  
  
 有关在 ATL 中使用连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
## <a name="see-also"></a>请参阅  
 [IConnectionPointImpl 类](../../atl/reference/iconnectionpointimpl-class.md)   
 [IConnectionPointContainerImpl 类](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)

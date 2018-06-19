---
title: IPropertyNotifySinkCP 类 |Microsoft 文档
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
ms.openlocfilehash: d9612cf65479e474b9a6e89a8f5a57ca078c9ed0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361621"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP 类
此类公开[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)作为可连接对象上的传出接口的接口。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T, class CDV = CComDynamicUnkArray>  
class IPropertyNotifySinkCP 
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```    
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IPropertyNotifySinkCP`。  
  
 `CDV`  
 类，用于管理连接点和其接收器之间的连接。 默认值是[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，它允许不受限制的连接。 你还可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md)，它指定固定的数量的连接。  
  
## <a name="remarks"></a>备注  
 `IPropertyNotifySinkCP` 继承通过其基类，所有方法[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)。  
  
 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)接口允许接收有关属性更改的通知接收器对象。 类`IPropertyNotifySinkCP`作为可连接对象上的传出接口公开此接口。 客户端必须实现`IPropertyNotifySink`接收器上的方法。  
  
 派生您的类从`IPropertyNotifySinkCP`如果想要创建连接点表示`IPropertyNotifySink`接口。  
  
 有关使用 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
## <a name="see-also"></a>请参阅  
 [IConnectionPointImpl 类](../../atl/reference/iconnectionpointimpl-class.md)   
 [IConnectionPointContainerImpl 类](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)

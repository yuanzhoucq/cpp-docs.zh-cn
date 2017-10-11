---
title: "CFirePropNotifyEvent 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
dev_langs:
- C++
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: c55726a1728185f699afbac4ba68a6dc0f70c2bf
ms.openlocfilehash: 1fb22263b877aaff3e30e56efff2a005bc024f2e
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent 类
此类提供方法通知控件属性更改有关的容器的接收器。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CFirePropNotifyEvent
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|（静态）通知的控件属性已更改的容器的接收器。|  
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|（静态）通知的控件属性即将更改的容器的接收器。|  
  
## <a name="remarks"></a>备注  
 `CFirePropNotifyEvent`有两种方法，以通知容器的接收器的控件属性已更改或即将更改。  
  
 如果实现控件的类派生自`IPropertyNotifySink`、`CFirePropNotifyEvent`方法进行调用时，调用`FireOnRequestEdit`或`FireOnChanged`。 如果你的控件类不派生自`IPropertyNotifySink`，对这些函数的调用返回`S_OK`。  
  
 有关创建控件的详细信息，请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
##  <a name="fireonchanged"></a>CFirePropNotifyEvent::FireOnChanged  
 通知所有连接[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)指定的对象属性已更改 （上对象的每个连接点） 的接口。  
  
```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 [in]指向**IUnknown**发送通知的对象。  
  
 *dispID*  
 [in]已更改的属性的标识符。  
  
### <a name="return-value"></a>返回值  
 一个标准`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 此函数可安全地调用即使你的控件不支持连接点。  
  
##  <a name="fireonrequestedit"></a>CFirePropNotifyEvent::FireOnRequestEdit  
 通知所有连接[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)即将更改指定的对象属性 （在该对象的每个连接点） 的接口。  
  
```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 [in]指向**IUnknown**发送通知的对象。  
  
 *dispID*  
 [in]要更改的属性的标识符。  
  
### <a name="return-value"></a>返回值  
 一个标准`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 此函数可安全地调用即使你的控件不支持连接点。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)


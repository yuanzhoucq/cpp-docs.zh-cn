---
title: "CFirePropNotifyEvent 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFirePropNotifyEvent
- ATL::CFirePropNotifyEvent
- ATL.CFirePropNotifyEvent
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 1511a9e9ba287d12aade7c393887c6b5f8880b96
ms.lasthandoff: 02/24/2017

---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent 类
此类提供用于通知与控件属性更改有关的容器的接收器的方法。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CFirePropNotifyEvent
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|（静态）通知已更改的控件属性的容器的接收器。|  
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|（静态）通知即将更改的控件属性的容器的接收器。|  
  
## <a name="remarks"></a>备注  
 `CFirePropNotifyEvent`有两种方法，以通知容器的接收器的控件属性已更改或即将更改。  
  
 如果实现您的控件的类派生自`IPropertyNotifySink`、`CFirePropNotifyEvent`方法进行调用时，调用`FireOnRequestEdit`或`FireOnChanged`。 如果您的控件类不源自`IPropertyNotifySink`，对这些函数的调用返回`S_OK`。  
  
 有关创建控件的详细信息，请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="a-namefireonchangeda--cfirepropnotifyeventfireonchanged"></a><a name="fireonchanged"></a>CFirePropNotifyEvent::FireOnChanged  
 通知所有连接[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) （上对象的每个连接点） 指定的对象属性已更改的接口。  
  
```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 [in]指向**IUnknown**发送通知的对象。  
  
 *dispID*  
 [in]已更改的属性的标识符。  
  
### <a name="return-value"></a>返回值  
 其中一个标准`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 此函数是安全地调用即使您的控件不支持连接点。  
  
##  <a name="a-namefireonrequestedita--cfirepropnotifyeventfireonrequestedit"></a><a name="fireonrequestedit"></a>CFirePropNotifyEvent::FireOnRequestEdit  
 通知所有连接[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)指定的对象属性是否将要发生更改 （在该对象的每个连接点） 的接口。  
  
```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 [in]指向**IUnknown**发送通知的对象。  
  
 *dispID*  
 [in]要更改的属性的标识符。  
  
### <a name="return-value"></a>返回值  
 其中一个标准`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 此函数是安全地调用即使您的控件不支持连接点。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)


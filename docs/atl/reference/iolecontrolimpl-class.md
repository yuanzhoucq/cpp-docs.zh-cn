---
title: "IOleControlImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOleControlImpl
dev_langs:
- C++
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
caps.latest.revision: 22
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5e63849a504b931de30141dd91af557f16c67fd8
ms.lasthandoff: 02/24/2017

---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl 类
此类提供的默认实现**IOleControl**接口和实现**IUnknown**。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>
class IOleControlImpl
```   
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IOleControlImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IOleControlImpl::FreezeEvents](#freezeevents)|指示忽略容器，或接受控件中的事件。|  
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|填写有关控件的键盘行为的信息。 ATL 实现返回**E_NOTIMPL**。|  
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|通知一个或多个容器的环境属性已更改一个控件。 ATL 实现返回`S_OK`。|  
|[IOleControlImpl::OnMnemonic](#onmnemonic)|通知控件用户已按指定的键击。 ATL 实现返回**E_NOTIMPL**。|  
  
## <a name="remarks"></a>备注  
 类`IOleControlImpl`提供的默认实现[IOleControl](http://msdn.microsoft.com/library/windows/desktop/ms694320)接口和实现**IUnknown**中调试设备信息发送给转储生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IOleControl`  
  
 `IOleControlImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="a-namefreezeeventsa--iolecontrolimplfreezeevents"></a><a name="freezeevents"></a>IOleControlImpl::FreezeEvents  
 在 ATL 的实现中，`FreezeEvents`递增控件类`m_nFreezeEvents`数据成员如果`bFreeze`是**TRUE**，并减少`m_nFreezeEvents`如果`bFreeze`是**FALSE**。  
  
```
HRESULT FreezeEvents(BOOL bFreeze);
```  
  
### <a name="remarks"></a>备注  
 `FreezeEvents`然后返回`S_OK`。  
  
 请参阅[IOleControl::FreezeEvents](http://msdn.microsoft.com/library/windows/desktop/ms678482)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetcontrolinfoa--iolecontrolimplgetcontrolinfo"></a><a name="getcontrolinfo"></a>IOleControlImpl::GetControlInfo  
 填写有关控件的键盘行为的信息。  
  
```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IOleControl:GetControlInfo](http://msdn.microsoft.com/library/windows/desktop/ms693730)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
##  <a name="a-nameonambientpropertychangea--iolecontrolimplonambientpropertychange"></a><a name="onambientpropertychange"></a>IOleControlImpl::OnAmbientPropertyChange  
 通知一个或多个容器的环境属性已更改一个控件。  
  
```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleControl::OnAmbientPropertyChange](http://msdn.microsoft.com/library/windows/desktop/ms690175)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonmnemonica--iolecontrolimplonmnemonic"></a><a name="onmnemonic"></a>IOleControlImpl::OnMnemonic  
 通知控件用户已按指定的键击。  
  
```
HRESULT OnMnemonic(LPMSG pMsg);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleControl::OnMnemonic](http://msdn.microsoft.com/library/windows/desktop/ms680699)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [IOleObjectImpl 类](../../atl/reference/ioleobjectimpl-class.md)   
 [ActiveX 控件接口](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [类概述](../../atl/atl-class-overview.md)


---
title: "IPointerInactiveImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPointerInactiveImpl
dev_langs:
- C++
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
caps.latest.revision: 21
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 05cf4b2247cabe713cfc6b0dd54c95c01e5bbddc
ms.lasthandoff: 02/24/2017

---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl 类
此类实现**IUnknown**和[IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712)接口方法。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>
class IPointerInactiveImpl
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IPointerInactiveImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|检索对象的当前激活策略。 ATL 实现返回**E_NOTIMPL**。|  
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|通知鼠标指针已移动到它上面，该对象，该值指示该对象可以激发鼠标事件。 ATL 实现返回**E_NOTIMPL**。|  
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|如果将鼠标指针的非活动状态的对象。 ATL 实现返回**E_NOTIMPL**。|  
  
## <a name="remarks"></a>备注  
 非活动状态的对象是指位于，只需加载或正在运行。 与活动的对象，不同的非活动状态的对象无法接收 Windows 鼠标和键盘消息。 因此，非活动对象使用的资源少，并且通常更有效。  
  
 [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712)接口允许对象以支持同时保持非活动状态的鼠标交互的最低级别。 此功能是对的控件特别有用。  
  
 类`IPointerInactiveImpl`实现`IPointerInactive`方法简单地返回**E_NOTIMPL**。 但是，它将实现**IUnknown**中调试设备信息发送给转储生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IPointerInactive`  
  
 `IPointerInactiveImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="a-namegetactivationpolicya--ipointerinactiveimplgetactivationpolicy"></a><a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy  
 检索对象的当前激活策略。  
  
```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IPointerInactive::GetActivationPolicy](http://msdn.microsoft.com/library/windows/desktop/ms692470)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameoninactivemousemovea--ipointerinactiveimploninactivemousemove"></a><a name="oninactivemousemove"></a>IPointerInactiveImpl::OnInactiveMouseMove  
 通知鼠标指针已移动到它上面，该对象，该值指示该对象可以激发鼠标事件。  
  
```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IPointerInactive::OnInactiveMouseMove](http://msdn.microsoft.com/library/windows/desktop/ms693374)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameoninactivesetcursora--ipointerinactiveimploninactivesetcursor"></a><a name="oninactivesetcursor"></a>IPointerInactiveImpl::OnInactiveSetCursor  
 如果将鼠标指针的非活动状态的对象。  
  
```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IPointerInactive::OnInactiveSetCursor](http://msdn.microsoft.com/library/windows/desktop/ms694336)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)


---
title: IPointerInactiveImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
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
ms.workload:
- cplusplus
ms.openlocfilehash: fe45700a941a8a59439b816124728f43e5f54f44
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl 类
此类实现**IUnknown**和[IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712)接口方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>
class IPointerInactiveImpl
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IPointerInactiveImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|检索对象的当前激活策略。 ATL 实现返回**E_NOTIMPL**。|  
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|通知鼠标指针已移动到它上面，，表示该对象的对象可以激发鼠标事件。 ATL 实现返回**E_NOTIMPL**。|  
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|设置鼠标指针的非活动状态的对象。 ATL 实现返回**E_NOTIMPL**。|  
  
## <a name="remarks"></a>备注  
 非活动状态的对象是指位于只需加载或正在运行。 与活动的对象，不同的非活动状态的对象无法接收 Windows 鼠标和键盘消息。 因此，非活动状态的对象使用的资源少，并且通常更高效。  
  
 [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712)接口允许对象支持同时保持非活动状态的鼠标交互的最低级别。 此功能很适合用于控件。  
  
 类`IPointerInactiveImpl`实现`IPointerInactive`方法通过只需返回**E_NOTIMPL**。 但是，它实现**IUnknown**信息发送给转储设备在调试生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IPointerInactive`  
  
 `IPointerInactiveImpl`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlctl.h  
  
##  <a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy  
 检索对象的当前激活策略。  
  
```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IPointerInactive::GetActivationPolicy](http://msdn.microsoft.com/library/windows/desktop/ms692470) Windows SDK 中。  
  
##  <a name="oninactivemousemove"></a>IPointerInactiveImpl::OnInactiveMouseMove  
 通知鼠标指针已移动到它上面，，表示该对象的对象可以激发鼠标事件。  
  
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
 请参阅[IPointerInactive::OnInactiveMouseMove](http://msdn.microsoft.com/library/windows/desktop/ms693374) Windows SDK 中。  
  
##  <a name="oninactivesetcursor"></a>IPointerInactiveImpl::OnInactiveSetCursor  
 设置鼠标指针的非活动状态的对象。  
  
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
 请参阅[IPointerInactive::OnInactiveSetCursor](http://msdn.microsoft.com/library/windows/desktop/ms694336) Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)

---
title: "IOleInPlaceObjectWindowlessImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetDropTarget
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::OnWindowMessage
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::SetObjectRects
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::UIDeactivate
dev_langs:
- C++
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f455172723be4f46751b45d244e74dda5fcacae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl 类
此类实现**IUnknown**并且提供了启用无窗口控件接收窗口消息并将参与拖放操作的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IOleInPlaceObjectWindowlessImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|使上下文相关帮助。 ATL 实现返回**E_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|提供`IDropTarget`支持拖放的就地活动状态，无窗口对象的接口。 ATL 实现返回**E_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|获取窗口句柄。|  
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|停用活动的就地控件。|  
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|将调度到处于就地活动状态的无窗口控件容器的消息。|  
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|重新激活以前已停用的控件。 ATL 实现返回**E_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|指示在就地控件的哪个部分可见。|  
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|停用并删除支持就地激活的用户界面。|  
  
## <a name="remarks"></a>备注  
 [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646)接口管理重新激活和停用中现有的控制，并确定控件中有多少应该是可见的。 [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304)接口启用无窗口控件接收窗口消息并将参与拖放操作。 类`IOleInPlaceObjectWindowlessImpl`提供的默认实现`IOleInPlaceObject`和`IOleInPlaceObjectWindowless`并实现**IUnknown**信息发送给转储设备在调试生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IOleInPlaceObjectWindowless`  
  
 `IOleInPlaceObjectWindowlessImpl`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp  
 返回**E_NOTIMPL**。  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059) Windows SDK 中。  
  
##  <a name="getdroptarget"></a>IOleInPlaceObjectWindowlessImpl::GetDropTarget  
 返回**E_NOTIMPL**。  
  
```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IOleInPlaceObjectWindowless::GetDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms678535) Windows SDK 中。  
  
##  <a name="getwindow"></a>IOleInPlaceObjectWindowlessImpl::GetWindow  
 容器调用此函数可获取控件的窗口句柄。  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>备注  
 某些容器不会使用已无窗口，即使它是当前窗口的控件。 在 ATL 的实现中，如果控件类的数据成员`m_bWasOnceWindowless`是**TRUE**，该函数将返回**E_FAIL**。 否则为如果*phwnd*不**NULL**，`GetWindow`设置\* *phwnd*到控件类的数据成员`m_hWnd`并返回`S_OK`.  
  
 请参阅[IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282) Windows SDK 中。  
  
##  <a name="inplacedeactivate"></a>IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate  
 由要停用的就地活动控件的容器调用。  
  
```
HRESULT InPlaceDeactivate(HWND* phwnd);
```  
  
### <a name="remarks"></a>备注  
 此方法执行具体取决于控件的状态的完整或部分停用。 如有必要，控件的用户界面已停用，并且销毁该控件的窗口中，如果有的话。 容器是收到通知，该控件处于不再就地活动状态。 **IOleInPlaceUIWindow**释放由容器用于协商菜单以及边框空间的接口。  
  
 请参阅[IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700) Windows SDK 中。  
  
##  <a name="onwindowmessage"></a>IOleInPlaceObjectWindowlessImpl::OnWindowMessage  
 将调度到处于就地活动状态的无窗口控件容器的消息。  
  
```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IOleInPlaceObjectWindowless::OnWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms693783) Windows SDK 中。  
  
##  <a name="reactivateandundo"></a>IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo  
 返回**E_NOTIMPL**。  
  
```
HRESULT ReactivateAndUndo();
```  
  
### <a name="remarks"></a>备注  
 请参阅[IOleInPlaceObject::ReactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms691372) Windows SDK 中。  
  
##  <a name="setobjectrects"></a>IOleInPlaceObjectWindowlessImpl::SetObjectRects  
 由要通知其大小和/或位置已更改的控件的容器调用。  
  
```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```  
  
### <a name="remarks"></a>备注  
 更新控件的`m_rcPos`数据成员和控件显示。 将显示仅与该剪辑区域相交的控件的部分。 如果以前剪切控件的显示，但已删除剪辑，则可以调用此函数进行重绘控件的完整视图。  
  
 请参阅[IOleInPlaceObject::SetObjectRects](http://msdn.microsoft.com/library/windows/desktop/ms683767) Windows SDK 中。  
  
##  <a name="uideactivate"></a>IOleInPlaceObjectWindowlessImpl::UIDeactivate  
 停用并删除支持就地激活的控件的用户界面。  
  
```
HRESULT UIDeactivate();
```  
  
### <a name="remarks"></a>备注  
 设置的控件类数据成员`m_bUIActive`到**FALSE**。 此操作的 ATL 实现函数始终返回`S_OK`。  
  
 请参阅[IOleInPlaceObject::UIDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms693348) Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [类概述](../../atl/atl-class-overview.md)

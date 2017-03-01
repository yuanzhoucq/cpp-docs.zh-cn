---
title: "IOleInPlaceObjectWindowlessImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOleInPlaceObjectWindowlessImpl
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 06ce03a896c9948bff14b4f91ae48000d07c3edd
ms.lasthandoff: 02/24/2017

---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl 类
此类实现**IUnknown**并且提供了启用无窗口控件接收窗口消息并将参与拖放操作的方法。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IOleInPlaceObjectWindowlessImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|使上下文相关帮助。 ATL 实现返回**E_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|提供`IDropTarget`支持拖放的处于就地活动状态，无窗口对象的接口。 ATL 实现返回**E_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|获取窗口句柄。|  
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|停用活动的就地控件。|  
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|将调度到处于就地活动状态的无窗口控件容器的消息。|  
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|重新激活以前已停用的控件。 ATL 实现返回**E_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|指示哪一部分就地控件可见。|  
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|停用并删除在用户界面中支持就地激活。|  
  
## <a name="remarks"></a>备注  
 [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646)接口管理重新激活和停用的适当地控件并确定控件中有多少应可见。 [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304)接口启用无窗口控件接收窗口消息并将参与拖放操作。 类`IOleInPlaceObjectWindowlessImpl`提供的默认实现`IOleInPlaceObject`和`IOleInPlaceObjectWindowless`并实现**IUnknown**中调试设备信息发送给转储生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IOleInPlaceObjectWindowless`  
  
 `IOleInPlaceObjectWindowlessImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="a-namecontextsensitivehelpa--ioleinplaceobjectwindowlessimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp  
 返回**E_NOTIMPL**。  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetdroptargeta--ioleinplaceobjectwindowlessimplgetdroptarget"></a><a name="getdroptarget"></a>IOleInPlaceObjectWindowlessImpl::GetDropTarget  
 返回**E_NOTIMPL**。  
  
```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IOleInPlaceObjectWindowless::GetDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms678535)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetwindowa--ioleinplaceobjectwindowlessimplgetwindow"></a><a name="getwindow"></a>IOleInPlaceObjectWindowlessImpl::GetWindow  
 容器将调用此函数可获取该控件的窗口句柄。  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>备注  
 一些容器将不适用于已无窗口，即使它是当前窗口的控件。 在 ATL 的实现中，如果控件类数据成员`m_bWasOnceWindowless`是**TRUE**，该函数将返回**E_FAIL**。 否则为如果*phwnd*不是**NULL**，`GetWindow`设置\* *phwnd*绑定到控件类数据成员`m_hWnd`，并返回`S_OK`。  
  
 请参阅[IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameinplacedeactivatea--ioleinplaceobjectwindowlessimplinplacedeactivate"></a><a name="inplacedeactivate"></a>IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate  
 若要停用处于就地活动控件的容器由调用。  
  
```
HRESULT InPlaceDeactivate(HWND* phwnd);
```  
  
### <a name="remarks"></a>备注  
 此方法执行具体取决于控件的状态的完整或部分停用。 如有必要，控件的用户界面已停用，并销毁该控件的窗口中，如果有的话。 容器将收到通知，该控件处于不能再就地活动状态。 **IOleInPlaceUIWindow**释放由容器用来协商菜单，并边框空间的接口。  
  
 请参阅[IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonwindowmessagea--ioleinplaceobjectwindowlessimplonwindowmessage"></a><a name="onwindowmessage"></a>IOleInPlaceObjectWindowlessImpl::OnWindowMessage  
 将从容器到处于就地活动状态的无窗口控件的消息调度。  
  
```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IOleInPlaceObjectWindowless::OnWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms693783)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namereactivateandundoa--ioleinplaceobjectwindowlessimplreactivateandundo"></a><a name="reactivateandundo"></a>IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo  
 返回**E_NOTIMPL**。  
  
```
HRESULT ReactivateAndUndo();
```  
  
### <a name="remarks"></a>备注  
 请参阅[IOleInPlaceObject::ReactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms691372)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetobjectrectsa--ioleinplaceobjectwindowlessimplsetobjectrects"></a><a name="setobjectrects"></a>IOleInPlaceObjectWindowlessImpl::SetObjectRects  
 由容器以通知其大小和/或位置已更改该控件调用。  
  
```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```  
  
### <a name="remarks"></a>备注  
 可更新控件的`m_rcPos`数据成员和控件显示。 将显示只与该剪辑区域相交的控件的部分。 如果先前剪切控件的显示，但剪辑已被删除，则可以调用此函数进行重绘该控件的完整视图。  
  
 请参阅[IOleInPlaceObject::SetObjectRects](http://msdn.microsoft.com/library/windows/desktop/ms683767)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameuideactivatea--ioleinplaceobjectwindowlessimpluideactivate"></a><a name="uideactivate"></a>IOleInPlaceObjectWindowlessImpl::UIDeactivate  
 停用并删除支持就地激活的控件的用户界面。  
  
```
HRESULT UIDeactivate();
```  
  
### <a name="remarks"></a>备注  
 设置控件类数据成员`m_bUIActive`到**FALSE**。 ATL 实施此函数始终返回`S_OK`。  
  
 请参阅[IOleInPlaceObject::UIDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms693348)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [类概述](../../atl/atl-class-overview.md)


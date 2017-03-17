---
title: "IOleInPlaceActiveObjectImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::EnableModeless
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnDocWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnFrameWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ResizeBorder
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::TranslateAccelerator
dev_langs:
- C++
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
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
ms.openlocfilehash: 766ac40bb0a09902914feab1acc54a960261a768
ms.lasthandoff: 02/24/2017

---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInPlaceActiveObjectImpl 类
此类提供，可帮助在就地控件与图像容器之间的通信的方法。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>
class IOleInPlaceActiveObjectImpl
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IOleInPlaceActiveObjectImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|使上下文相关帮助。 ATL 实现返回**E_NOTIMPL**。|  
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|启用无模式对话框。 ATL 实现返回`S_OK`。|  
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|获取窗口句柄。|  
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|通知控件容器的文档窗口处于激活或停用时。 ATL 实现返回`S_OK`。|  
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|通知控件容器的顶层框架窗口在激活或停用。 ATL 实现将返回|  
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|通知控件需要调整其边框的大小。 ATL 实现返回`S_OK`。|  
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|处理菜单从容器的加速键消息。 ATL 实现返回**E_NOTIMPL**。|  
  
  
## <a name="remarks"></a>备注  
 [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299)界面可帮助在就地控件与图像容器之间的通信; 例如，进行通信的控制和容器，活动状态，并通知该控件需要调整自身大小。 类`IOleInPlaceActiveObjectImpl`提供的默认实现`IOleInPlaceActiveObject`并支持**IUnknown**中调试设备信息发送给转储生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IOleInPlaceActiveObject`  
  
 `IOleInPlaceActiveObjectImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>IOleInPlaceActiveObjectImpl::ContextSensitiveHelp  
 使上下文相关帮助。  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="enablemodeless"></a>IOleInPlaceActiveObjectImpl::EnableModeless  
 启用无模式对话框。  
  
```
HRESULT EnableModeless(BOOL fEnable);
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getwindow"></a>IOleInPlaceActiveObjectImpl::GetWindow  
 容器将调用此函数可获取该控件的窗口句柄。  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>备注  
 一些容器将不适用于已无窗口，即使它是当前窗口的控件。 在 ATL 的实现中，如果**CComControl::m_bWasOnceWindowless**数据成员是**TRUE**，该函数将返回**E_FAIL**。 否则为如果\* *phwnd*不是**NULL**，`GetWindow`分配*phwnd*绑定到控件类数据成员`m_hWnd`，并返回`S_OK`。  
  
 请参阅[IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="ondocwindowactivate"></a>IOleInPlaceActiveObjectImpl::OnDocWindowActivate  
 通知控件容器的文档窗口处于激活或停用时。  
  
```
HRESULT OnDocWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onframewindowactivate"></a>IOleInPlaceActiveObjectImpl::OnFrameWindowActivate  
 通知控件容器的顶层框架窗口在激活或停用。  
  
```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="resizeborder"></a>IOleInPlaceActiveObjectImpl::ResizeBorder  
 通知控件需要调整其边框的大小。  
  
```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="translateaccelerator"></a>IOleInPlaceActiveObjectImpl::TranslateAccelerator  
 处理菜单从容器的加速键消息。  
  
```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```  
  
### <a name="return-value"></a>返回值  
 此方法支持下列返回值：  
  
 `S_OK`如果消息已成功转换。  
  
 **S_FALSE**如果不转换该消息。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)  
 [ActiveX 控件接口](http://msdn.microsoft.com/library/windows/desktop/ms692724)  
 [类概述](../../atl/atl-class-overview.md)


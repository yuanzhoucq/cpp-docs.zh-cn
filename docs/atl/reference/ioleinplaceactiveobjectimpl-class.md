---
title: IOleInPlaceActiveObjectImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0d98b8dd082a09de461452b43b70ddeb9431abe
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInPlaceActiveObjectImpl 类
此类提供，可帮助在就地控件与其容器之间的通信的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>
class IOleInPlaceActiveObjectImpl
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IOleInPlaceActiveObjectImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|使上下文相关帮助。 ATL 实现返回**E_NOTIMPL**。|  
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|启用无模式对话框。 ATL 实现返回`S_OK`。|  
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|获取窗口句柄。|  
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|当激活或停用容器的文档窗口时，请通知控件。 ATL 实现返回`S_OK`。|  
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|当激活或停用容器的顶级框架窗口时，请通知控件。 ATL 实现返回|  
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|通知控件需要调整其边框的大小。 ATL 实现返回`S_OK`。|  
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|处理从容器的菜单快捷键消息。 ATL 实现返回**E_NOTIMPL**。|  
  
  
## <a name="remarks"></a>备注  
 [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299)界面可帮助在就地控件与其容器之间的通信; 例如，通信活动状态的控件和容器，并通知控件它需要调整大小本身。 类`IOleInPlaceActiveObjectImpl`提供的默认实现`IOleInPlaceActiveObject`并支持**IUnknown**信息发送给转储设备在调试生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IOleInPlaceActiveObject`  
  
 `IOleInPlaceActiveObjectImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>  IOleInPlaceActiveObjectImpl::ContextSensitiveHelp  
 使上下文相关帮助。  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059) Windows SDK 中。  
  
##  <a name="enablemodeless"></a>  IOleInPlaceActiveObjectImpl::EnableModeless  
 启用无模式对话框。  
  
```
HRESULT EnableModeless(BOOL fEnable);
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115) Windows SDK 中。  
  
##  <a name="getwindow"></a>  IOleInPlaceActiveObjectImpl::GetWindow  
 容器调用此函数可获取控件的窗口句柄。  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>备注  
 某些容器不会使用已无窗口，即使它是当前窗口的控件。 在 ATL 的实现中，如果**CComControl::m_bWasOnceWindowless**数据成员是**TRUE**，该函数将返回**E_FAIL**。 否则为如果\* *phwnd*不**NULL**，`GetWindow`分配*phwnd*到控件类的数据成员`m_hWnd`并返回`S_OK`.  
  
 请参阅[IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282) Windows SDK 中。  
  
##  <a name="ondocwindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnDocWindowActivate  
 当激活或停用容器的文档窗口时，请通知控件。  
  
```
HRESULT OnDocWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281) Windows SDK 中。  
  
##  <a name="onframewindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnFrameWindowActivate  
 当激活或停用容器的顶级框架窗口时，请通知控件。  
  
```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[ioleinplaceactiveobject:: Onframewindowactivate](http://msdn.microsoft.com/library/windows/desktop/ms683969) Windows SDK 中。  
  
##  <a name="resizeborder"></a>  IOleInPlaceActiveObjectImpl::ResizeBorder  
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
 请参阅[IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053) Windows SDK 中。  
  
##  <a name="translateaccelerator"></a>  IOleInPlaceActiveObjectImpl::TranslateAccelerator  
 处理从容器的菜单快捷键消息。  
  
```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```  
  
### <a name="return-value"></a>返回值  
 此方法支持下列返回值：  
  
 `S_OK` 如果消息已成功转换。  
  
 **S_FALSE**如果消息已不会进行转换。  
  
### <a name="remarks"></a>备注  
 请参阅[ioleinplaceactiveobject:: Translateaccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)  
 [ActiveX 控件接口](http://msdn.microsoft.com/library/windows/desktop/ms692724)  
 [类概述](../../atl/atl-class-overview.md)

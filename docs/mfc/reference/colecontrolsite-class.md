---
title: "COleControlSite Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleControlSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleControlSite class"
ms.assetid: 43970644-5eab-434a-8ba6-56d144ff1e3f
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# COleControlSite Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供用于自定义客户端控件接口支持。  
  
## 语法  
  
```  
class COleControlSite : public CCmdTarget  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleControlSite::COleControlSite](../Topic/COleControlSite::COleControlSite.md)|构造 `COleControlSite` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleControlSite::BindDefaultProperty](../Topic/COleControlSite::BindDefaultProperty.md)|将承载控件的默认属性设置为数据源。|  
|[COleControlSite::BindProperty](../Topic/COleControlSite::BindProperty.md)|将承载的控件的属性设置为数据源。|  
|[COleControlSite::CreateControl](../Topic/COleControlSite::CreateControl.md)|创建一个承载ActiveX控件。|  
|[COleControlSite::DestroyControl](../Topic/COleControlSite::DestroyControl.md)|在销毁承载的控件。|  
|[COleControlSite::DoVerb](../Topic/COleControlSite::DoVerb.md)|执行所承载控件的给定谓词。|  
|[COleControlSite::EnableDSC](../Topic/COleControlSite::EnableDSC.md)|启用控制站点的数据源。|  
|[COleControlSite::EnableWindow](../Topic/COleControlSite::EnableWindow.md)|启用控制站点。|  
|[COleControlSite::FreezeEvents](../Topic/COleControlSite::FreezeEvents.md)|指定控件网站是否接受事件。|  
|[COleControlSite::GetDefBtnCode](../Topic/COleControlSite::GetDefBtnCode.md)|检索所承载控件的默认按钮代码。|  
|[COleControlSite::GetDlgCtrlID](../Topic/COleControlSite::GetDlgCtrlID.md)|检索控件的标识符。|  
|[COleControlSite::GetEventIID](../Topic/COleControlSite::GetEventIID.md)|检索一事件接口的ID承载的控件的。|  
|[COleControlSite::GetExStyle](../Topic/COleControlSite::GetExStyle.md)|检索控件站点的扩展样式。|  
|[COleControlSite::GetProperty](../Topic/COleControlSite::GetProperty.md)|检索所承载的控件的特定属性。|  
|[COleControlSite::GetStyle](../Topic/COleControlSite::GetStyle.md)|检索控件站点的样式。|  
|[COleControlSite::GetWindowText](../Topic/COleControlSite::GetWindowText.md)|检索所承载的控件的文本。|  
|[COleControlSite::InvokeHelper](../Topic/COleControlSite::InvokeHelper.md)|调用所承载的控件的特定方法。|  
|[COleControlSite::InvokeHelperV](../Topic/COleControlSite::InvokeHelperV.md)|调用承载的控件的特定方法与变量的参数列表。|  
|[COleControlSite::IsDefaultButton](../Topic/COleControlSite::IsDefaultButton.md)|确定控件是否在窗口的默认按钮。|  
|[COleControlSite::IsWindowEnabled](../Topic/COleControlSite::IsWindowEnabled.md)|检查控制站点的可视状态。|  
|[COleControlSite::ModifyStyle](../Topic/COleControlSite::ModifyStyle.md)|修改控制站点的当前扩展样式。|  
|[COleControlSite::ModifyStyleEx](../Topic/COleControlSite::ModifyStyleEx.md)|修改控制站点的当前样式。|  
|[COleControlSite::MoveWindow](../Topic/COleControlSite::MoveWindow.md)|更改控制站点的位置。|  
|[COleControlSite::QuickActivate](../Topic/COleControlSite::QuickActivate.md)|提高激活所承载的控件。|  
|[COleControlSite::SafeSetProperty](../Topic/COleControlSite::SafeSetProperty.md)|将控件的属性或方法，而没有引发异常的可能性。|  
|[COleControlSite::SetDefaultButton](../Topic/COleControlSite::SetDefaultButton.md)|在窗口中设置默认按钮。|  
|[COleControlSite::SetDlgCtrlID](../Topic/COleControlSite::SetDlgCtrlID.md)|检索控件的标识符。|  
|[COleControlSite::SetFocus](../Topic/COleControlSite::SetFocus.md)|将焦点设置到控制站点。|  
|[COleControlSite::SetProperty](../Topic/COleControlSite::SetProperty.md)|设置承载的控件的特定属性。|  
|[COleControlSite::SetPropertyV](../Topic/COleControlSite::SetPropertyV.md)|设置承载的控件的特定属性与变量的参数列表。|  
|[COleControlSite::SetWindowPos](../Topic/COleControlSite::SetWindowPos.md)|设置控制站点的位置。|  
|[COleControlSite::SetWindowText](../Topic/COleControlSite::SetWindowText.md)|设置承载的控件的文本。|  
|[COleControlSite::ShowWindow](../Topic/COleControlSite::ShowWindow.md)|显示或隐藏控件站点。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[COleControlSite::GetControlInfo](../Topic/COleControlSite::GetControlInfo.md)|检索键盘信息和助记键所承载控件的。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COleControlSite::m\_bIsWindowless](../Topic/COleControlSite::m_bIsWindowless.md)|确定承载的控件是无窗口控件。|  
|[COleControlSite::m\_ctlInfo](../Topic/COleControlSite::m_ctlInfo.md)|包含有关处理为控件的键盘的信息。|  
|[COleControlSite::m\_dwEventSink](../Topic/COleControlSite::m_dwEventSink.md)|控件的cookie连接点。|  
|[COleControlSite::m\_dwMiscStatus](../Topic/COleControlSite::m_dwMiscStatus.md)|承载的控件的混合状态。|  
|[COleControlSite::m\_dwPropNotifySink](../Topic/COleControlSite::m_dwPropNotifySink.md)|控件的 `IPropertyNotifySink` cookie。|  
|[COleControlSite::m\_dwStyle](../Topic/COleControlSite::m_dwStyle.md)|承载的控件的样式。|  
|[COleControlSite::m\_hWnd](../Topic/COleControlSite::m_hWnd.md)|控制站点的句柄。|  
|[COleControlSite::m\_iidEvents](../Topic/COleControlSite::m_iidEvents.md)|事件接口的ID承载的控件的。|  
|[COleControlSite::m\_nID](../Topic/COleControlSite::m_nID.md)|承载的控件的ID。|  
|[COleControlSite::m\_pActiveObject](../Topic/COleControlSite::m_pActiveObject.md)|对所承载的控件的 `IOleInPlaceActiveObject` 对象的指针。|  
|[COleControlSite::m\_pCtrlCont](../Topic/COleControlSite::m_pCtrlCont.md)|承载的控件的容器。|  
|[COleControlSite::m\_pInPlaceObject](../Topic/COleControlSite::m_pInPlaceObject.md)|对所承载的控件的 `IOleInPlaceObject` 对象的指针。|  
|[COleControlSite::m\_pObject](../Topic/COleControlSite::m_pObject.md)|对控件的 `IOleObjectInterface` 接口的指针。|  
|[COleControlSite::m\_pWindowlessObject](../Topic/COleControlSite::m_pWindowlessObject.md)|对控件的 `IOleInPlaceObjectWindowless` 接口的指针。|  
|[COleControlSite::m\_pWndCtrl](../Topic/COleControlSite::m_pWndCtrl.md)|对于windows对象的指针承载的控件的。|  
|[COleControlSite::m\_rect](../Topic/COleControlSite::m_rect.md)|控制站点的大小。|  
  
## 备注  
 此支持是嵌入ActiveX控件获取有关位置的其容器提供其显示站点、其标记、用户界面、其环境属性和其他资源的信息和区域的主要方式。  `COleControlSite` 完全实现 [IOleControlSite](http://msdn.microsoft.com/library/windows/desktop/ms688502)，[IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)，[IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706)，[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)，**IBoundObjectSite**，**INotifyDBEvents**，[IRowSetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) 接口。  此外，IDispatch接口\(提供环境属性和事件接收器支持\)还作为来实现。  
  
 使用 `COleControlSite`，若要创建ActiveX控件站点，从 `COleControlSite`派生选件类。  在您的 `CWnd`\-容器\(例如，您的对话框\)重写的派生类 **CWnd::CreateControlSite** 功能。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlSite`  
  
## 要求  
 **Header:** afxocc.h  
  
## 请参阅  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleControlContainer Class](../../mfc/reference/colecontrolcontainer-class.md)
---
title: "COleControlContainer Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleControlContainer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件容器 [C++], control site"
  - "COleControlContainer class"
  - "自定义控件 [MFC], sites"
ms.assetid: f7ce9246-0fb7-4f07-a83a-6c2390d0fdf8
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleControlContainer Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

作为ActiveX控件的控件容器。  
  
## 语法  
  
```  
class COleControlContainer : public CCmdTarget  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleControlContainer::COleControlContainer](../Topic/COleControlContainer::COleControlContainer.md)|构造 `COleControlContainer` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleControlContainer::AttachControlSite](../Topic/COleControlContainer::AttachControlSite.md)|创建一个控件站点，承载的容器。|  
|[COleControlContainer::BroadcastAmbientPropertyChange](../Topic/COleControlContainer::BroadcastAmbientPropertyChange.md)|通知所有承载的控件的一个环境属性已更改。|  
|[COleControlContainer::CheckDlgButton](../Topic/COleControlContainer::CheckDlgButton.md)|修改指定的按钮控件。|  
|[COleControlContainer::CheckRadioButton](../Topic/COleControlContainer::CheckRadioButton.md)|选择组的指定单选按钮。|  
|[COleControlContainer::CreateControl](../Topic/COleControlContainer::CreateControl.md)|创建一个承载ActiveX控件。|  
|[COleControlContainer::CreateOleFont](../Topic/COleControlContainer::CreateOleFont.md)|创建OLE字体。|  
|[COleControlContainer::FindItem](../Topic/COleControlContainer::FindItem.md)|返回指定控件的自定义站点。|  
|[COleControlContainer::FreezeAllEvents](../Topic/COleControlContainer::FreezeAllEvents.md)|确定控制站点是否接受事件。|  
|[COleControlContainer::GetAmbientProp](../Topic/COleControlContainer::GetAmbientProp.md)|检索具有指定的单个属性。|  
|[COleControlContainer::GetDlgItem](../Topic/COleControlContainer::GetDlgItem.md)|检索指定的对话框控件。|  
|[COleControlContainer::GetDlgItemInt](../Topic/COleControlContainer::GetDlgItemInt.md)|检索指定的对话框控件的值。|  
|[COleControlContainer::GetDlgItemText](../Topic/COleControlContainer::GetDlgItemText.md)|检索指定的对话框控件的说明。|  
|[COleControlContainer::HandleSetFocus](../Topic/COleControlContainer::HandleSetFocus.md)|确定是否容器处理 `WM_SETFOCUS` 消息。|  
|[COleControlContainer::HandleWindowlessMessage](../Topic/COleControlContainer::HandleWindowlessMessage.md)|处理发送到无窗口控件。|  
|[COleControlContainer::IsDlgButtonChecked](../Topic/COleControlContainer::IsDlgButtonChecked.md)|确定指定的按钮的状态。|  
|[COleControlContainer::OnPaint](../Topic/COleControlContainer::OnPaint.md)|调用重新绘制容器的一部分。|  
|[COleControlContainer::OnUIActivate](../Topic/COleControlContainer::OnUIActivate.md)|调用，如果控件要激活的就地。|  
|[COleControlContainer::OnUIDeactivate](../Topic/COleControlContainer::OnUIDeactivate.md)|调用时，将停用控件。|  
|[COleControlContainer::ScrollChildren](../Topic/COleControlContainer::ScrollChildren.md)|调用由结构，在滚动消息来自子窗口收到。|  
|[COleControlContainer::SendDlgItemMessage](../Topic/COleControlContainer::SendDlgItemMessage.md)|将消息发送给指定的控件。|  
|[COleControlContainer::SetDlgItemInt](../Topic/COleControlContainer::SetDlgItemInt.md)|设置特定的控件的值。|  
|[COleControlContainer::SetDlgItemText](../Topic/COleControlContainer::SetDlgItemText.md)|将指定控件的文本。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COleControlContainer::m\_crBack](../Topic/COleControlContainer::m_crBack.md)|容器的背景色。|  
|[COleControlContainer::m\_crFore](../Topic/COleControlContainer::m_crFore.md)|容器的前景色。|  
|[COleControlContainer::m\_listSitesOrWnds](../Topic/COleControlContainer::m_listSitesOrWnds.md)|支持的控件站点的列表。|  
|[COleControlContainer::m\_nWindowlessControls](../Topic/COleControlContainer::m_nWindowlessControls.md)|承载的无窗口控件的数目。|  
|[COleControlContainer::m\_pOleFont](../Topic/COleControlContainer::m_pOleFont.md)|为自定义控件站点的OLE字体的指针。|  
|[COleControlContainer::m\_pSiteCapture](../Topic/COleControlContainer::m_pSiteCapture.md)|为了获得控制站点的指针。|  
|[COleControlContainer::m\_pSiteFocus](../Topic/COleControlContainer::m_pSiteFocus.md)|对当前输入焦点的控件的指针。|  
|[COleControlContainer::m\_pSiteUIActive](../Topic/COleControlContainer::m_pSiteUIActive.md)|对当前就地激活的控件的指针。|  
|[COleControlContainer::m\_pWnd](../Topic/COleControlContainer::m_pWnd.md)|指向实现控件容器的窗口。|  
|[COleControlContainer::m\_siteMap](../Topic/COleControlContainer::m_siteMap.md)|站点地图。|  
  
## 备注  
 这是通过提供完成一个或多个ActiveX控件网站支持\(实现 `COleControlSite`）。  `COleControlContainer` 完全实现 [IOleInPlaceFrame](http://msdn.microsoft.com/library/windows/desktop/ms692770) 和 [IOleContainer](http://msdn.microsoft.com/library/windows/desktop/ms690103) 接口，允许包含的ActiveX控件执行其限定为就地项目。  
  
 通常，此选件类与 `COccManager` 和 `COleControlSite` 结合使用实现自定义ActiveX控件容器，有一个或多个ActiveX控件的自定义站点的。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlContainer`  
  
## 要求  
 **Header:** afxocc.h  
  
## 请参阅  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleControlSite Class](../../mfc/reference/colecontrolsite-class.md)   
 [COccManager Class](../../mfc/reference/coccmanager-class.md)
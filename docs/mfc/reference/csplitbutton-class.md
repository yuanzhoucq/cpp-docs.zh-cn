---
title: "CSplitButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSplitButton class"
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSplitButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CSplitButton` 选件类表示拆分按钮控件。  拆分按钮控件执行一个默认行为，当用户单击按钮时的主要部件，并显示下拉菜单，当用户单击按钮的下拉箭头时。  
  
## 语法  
  
```  
class CSplitButton : public CButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSplitButton::CSplitButton](../Topic/CSplitButton::CSplitButton.md)|构造 `CSplitButton` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSplitButton::Create](../Topic/CSplitButton::Create.md)|使用指定的样式创建拆分按钮控件并将其附加到当前 `CSplitButton` 对象。|  
|[CSplitButton::SetDropDownMenu](../Topic/CSplitButton::SetDropDownMenu.md)|定位到突出显示的下拉菜单，当用户单击当前拆分按钮控件的下拉箭头时。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CSplitButton::OnDropDown](../Topic/CSplitButton::OnDropDown.md)|处理该系统发送的 `BCN_DROPDOWN` 通知用户单击当前拆分按钮控件的下拉箭头。|  
  
## 备注  
 `CSplitButton` 选件类从 [CButton](../../mfc/reference/cbutton-class.md) 选件类派生。  拆分按钮控件是样式是 `BS_SPLITBUTTON`的按钮控件。  当用户单击下拉箭头时，它显示自定义菜单。  有关更多信息，请参见 [按钮样式](http://msdn.microsoft.com/library/windows/desktop/bb775951)的 `BS_SPLITBUTTON` 和 `BS_DEFSPLITBUTTON` 样式。  
  
 下图显示包含一个页导航控件和一个\(1\)拆分按钮控件的对话框。  此根\(2\)下拉箭头已单击了，并且该\(3\)子菜单显示。  
  
 ![具有拆分按钮和页导航控件的对话框。](../../mfc/reference/media/splitbutton_pager.png "SplitButton\_Pager")  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CSplitButton`  
  
## 要求  
 **标头:** afxcmn.h  
  
 此选件类在 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] 和更高版本支持。  
  
 此选件类的其他要求。[Windows Vista 公共控件的生成要求](../../mfc/build-requirements-for-windows-vista-common-controls.md)所述。  
  
## 请参阅  
 [CSplitButton Class](../../mfc/reference/csplitbutton-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)
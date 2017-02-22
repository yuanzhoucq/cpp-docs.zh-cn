---
title: "CMFCDesktopAlertWndInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCDesktopAlertWndInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDesktopAlertWndInfo class"
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCDesktopAlertWndInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCDesktopAlertWndInfo` 类与 [CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md) 类一起使用。  它指定显示的控件，如果桌面通知窗口弹出窗口。  
  
## 语法  
  
```  
class CMFCDesktopAlertWndInfo  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCDesktopAlertWndInfo::operator\=](../Topic/CMFCDesktopAlertWndInfo::operator=.md)||  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCDesktopAlertWndInfo::m\_hIcon](../Topic/CMFCDesktopAlertWndInfo::m_hIcon.md)|对显示的图标的句柄。|  
|[CMFCDesktopAlertWndInfo::m\_nURLCmdID](../Topic/CMFCDesktopAlertWndInfo::m_nURLCmdID.md)|命令ID与桌面通知窗口的链接。|  
|[CMFCDesktopAlertWndInfo::m\_strText](../Topic/CMFCDesktopAlertWndInfo::m_strText.md)|在桌面通知窗口中显示的文本。|  
|[CMFCDesktopAlertWndInfo::m\_strURL](../Topic/CMFCDesktopAlertWndInfo::m_strURL.md)|在桌面通知窗口中显示的链接。|  
  
## 备注  
 `CMFCDesktopAlertWndInfo` 选件类传递给 [CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md) 方法指定在桌面通知窗口的默认对话框中显示的元素。  默认对话框可以包含三项:  
  
-   图标，通过调用 [CMFCDesktopAlertWndInfo::m\_hIcon](../Topic/CMFCDesktopAlertWndInfo::m_hIcon.md)设置。  
  
-   标签或文本消息，通过调用 [CMFCDesktopAlertWndInfo::m\_strText](../Topic/CMFCDesktopAlertWndInfo::m_strText.md)设置。  
  
-   链接，通过调用 [CMFCDesktopAlertWndInfo::m\_strURL](../Topic/CMFCDesktopAlertWndInfo::m_strURL.md)设置。  若要设置执行的命令，用于在单击链接时，请调用 [CMFCDesktopAlertWndInfo::m\_nURLCmdID](../Topic/CMFCDesktopAlertWndInfo::m_nURLCmdID.md)。  
  
 如果默认对话框是不够的，则可以创建自定义对话框并向其传递到 [CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md) 方法而不是使用此选件类。  有关更多信息，请参见 [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md)。  
  
## 示例  
 下面的示例在 `CMFCDesktopAlertWndInfo` 选件类演示如何使用各种成员。  示例演示如何设置句柄显示的图标，在桌面通知窗口、链接显示在桌面通知窗口和命令ID显示与桌面通知窗口的链接的文本。  此示例是 [桌面通知演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/CPP/cmfcdesktopalertwndinfo-class_1.cpp)]  
  
## 继承层次结构  
 [CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)  
  
## 要求  
 **标头:** afxDesktopAlertDialog.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md)   
 [CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md)   
 [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md)
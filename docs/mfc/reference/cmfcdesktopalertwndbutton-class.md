---
title: "CMFCDesktopAlertWndButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCDesktopAlertWndButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDesktopAlertWndButton class"
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CMFCDesktopAlertWndButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允许按钮添加到桌面通知对话框。  
  
## 语法  
  
```  
class CMFCDesktopAlertWndButton : public CMFCButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|默认构造函数。|  
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|析构函数。|  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCDesktopAlertWndButton::IsCaptionButton](../Topic/CMFCDesktopAlertWndButton::IsCaptionButton.md)|确定按钮是否在通知对话框的声明区域中显示。|  
|[CMFCDesktopAlertWndButton::IsCloseButton](../Topic/CMFCDesktopAlertWndButton::IsCloseButton.md)|确定按钮是否关闭警报对话框。|  
  
### 数据成员  
  
|||  
|-|-|  
|名称|说明|  
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|指定的布尔值按钮是否在通知对话框的声明区域中显示。|  
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|指定的布尔值按钮是否关闭警报对话框。|  
  
### 备注  
 默认情况下，该构造函数将 `m_bIsCaptionButton` 和 `m_bIsCloseButton` 数据成员设置为 `FALSE`。  如果按钮在通知对话框的声明区域，确定父 `CMFCDesktopAlertDialog` 对象设置 `m_bIsCaptionButton` 到 `TRUE`。  `CMFCDesktopAlertDialog` 选件类创建用作按钮关闭警报对话框并设置 `m_bIsCloseButton` 到 `TRUE`的一 `CMFCDesktopAlertWndButton` 对象。  
  
 因为这样做会将所有按钮，请向 `CMFCDesktopAlertDialog` 对象的 `CMFCDesktopAlertWndButton` 对象。  有关 `CMFCDesktopAlertDialog`的更多信息，请参见[CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md)。  
  
## 示例  
 下面的示例在 `CMFCDesktopAlertWndButton` 选件类演示如何使用 `SetImage` 方法。  此代码段是 [桌面通知演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/CPP/cmfcdesktopalertwndbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/CPP/cmfcdesktopalertwndbutton-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)  
  
## 要求  
 **标头:** afxdesktopalertwnd.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md)
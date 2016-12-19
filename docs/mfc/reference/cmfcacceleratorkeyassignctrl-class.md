---
title: "CMFCAcceleratorKeyAssignCtrl Class | Microsoft Docs"
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
  - "CMFCAcceleratorKeyAssignCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCAcceleratorKeyAssignCtrl class"
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
caps.latest.revision: 33
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCAcceleratorKeyAssignCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCAcceleratorKeyAssignCtrl` 类会扩展 [CEdit Class](../../mfc/reference/cedit-class.md)以支持额外的系统按钮，如 ALT、CONTROL 和 SHIFT。  
  
## 语法  
  
```  
class CMFCAcceleratorKeyAssignCtrl : public CEdit  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](../Topic/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl.md)|构造 `CMFCAcceleratorKeyAssignCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](../Topic/CMFCAcceleratorKeyAssignCtrl::GetAccel.md)|检索 `CMFCAcceleratorKeyAssignCtrl` 对象中按下的快捷键的 `ACCEL` 结构。|  
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](../Topic/CMFCAcceleratorKeyAssignCtrl::IsFocused.md)||  
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](../Topic/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined.md)|确定是否已定义快捷键。|  
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](../Topic/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage.md)|在窗口消息被发送到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数之前，由 [CWinApp](../../mfc/reference/cwinapp-class.md) 类用于对该窗口消息进行转换。  （重写 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。）|  
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](../Topic/CMFCAcceleratorKeyAssignCtrl::ResetKey.md)|重置快捷键。|  
  
## 备注  
 此类通过支持快捷键（也称为加速键）来扩展 `CEdit` 类的功能。  `CMFCAcceleratorKeyAssignCtrl` 类具有 [CEdit Class](../../mfc/reference/cedit-class.md)的功能，它还能识别系统按钮。  
  
 此类会将物理快捷键组合映射到字符串值。  例如，假定键组合 ALT \+ B 映射到字符串“Alt \+ B”。  当用户按下 `CMFCAcceleratorKeyAssignCtrl` 对象中的此键组合时，会向用户显示“Alt \+ B”。  有关快捷键和字符串格式之间的映射的详细信息，请参阅 [CMFCAcceleratorKey Class](../../mfc/reference/cmfcacceleratorkey-class.md)。  
  
## 示例  
 下列示例演示如何构造 `CMFCAcceleratorKeyAssignCtrl` 对象并使用其 `ResetKey` 方法来重置快捷键。  
  
 [!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/CPP/cmfcacceleratorkeyassignctrl-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)  
  
## 要求  
 **标头：**afxacceleratorkeyassignctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCAcceleratorKey Class](../../mfc/reference/cmfcacceleratorkey-class.md)
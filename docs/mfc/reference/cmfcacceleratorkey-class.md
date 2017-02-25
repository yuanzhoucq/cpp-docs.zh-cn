---
title: "CMFCAcceleratorKey Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCAcceleratorKey"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCAcceleratorKey class"
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
caps.latest.revision: 36
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 38
---
# CMFCAcceleratorKey Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现格式设置虚拟个映射的键和的帮助器选件类。  
  
## 语法  
  
```  
class CMFCAcceleratorKey : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCAcceleratorKey::CMFCAcceleratorKey](../Topic/CMFCAcceleratorKey::CMFCAcceleratorKey.md)|构造 `CMFCAcceleratorKey` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCAcceleratorKey::Format](../Topic/CMFCAcceleratorKey::Format.md)|转换ACCEL framework为它的可视化表示形式。|  
|[CMFCAcceleratorKey::SetAccelerator](../Topic/CMFCAcceleratorKey::SetAccelerator.md)|设置 `CMFCAcceleratorKey` 对象的热键。|  
  
## 备注  
 也称为快捷键都热键。  如果要显示用户输入的键盘快捷键，[CMFCAcceleratorKeyAssignCtrl Class](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) 映射键盘快捷键，例如Alt\+Shift\+S，对自定义文本格式，如“Alt \+ SHIFT \+ S”。  每 `CMFCAcceleratorKey` 对象映射一个热键到文本格式。  
  
 有关如何使用热键和快捷键对应表的更多信息，请参见[CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md)。  
  
## 示例  
 下面的示例演示如何构造 `CMFCAcceleratorKey` 对象以及如何使用其 `Format` 方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/CPP/cmfcacceleratorkey-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)  
  
## 要求  
 **标头:** afxacceleratorkey.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md)
---
title: "CPaintDC Class | Microsoft Docs"
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
  - "CPaintDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPaintDC class"
  - "OnPaint handler"
  - "WM_PAINT message"
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPaintDC Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从 [CDC](../../mfc/reference/cdc-class.md)派生的设备上下文选件类。  
  
## 语法  
  
```  
class CPaintDC : public CDC  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CPaintDC::CPaintDC](../Topic/CPaintDC::CPaintDC.md)|构造 `CPaintDC` 连接到指定的 [CWnd](../../mfc/reference/cwnd-class.md)。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CPaintDC::m\_ps](../Topic/CPaintDC::m_ps.md)|包含一些 [PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md) 绘制工作区。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CPaintDC::m\_hWnd](../Topic/CPaintDC::m_hWnd.md)|此 `CPaintDC` 对象附加 `HWND`。|  
  
## 备注  
 它执行 [CWnd::BeginPaint](../Topic/CWnd::BeginPaint.md) 在构造时和 [CWnd::EndPaint](../Topic/CWnd::EndPaint.md) 在销毁时。  
  
 当响应 [WM\_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) 消息，通常 `CPaintDC` 对象在您的 `OnPaint` 消息处理程序成员函数时，只能使用。  
  
 有关使用 `CPaintDC`的更多信息，请参见 [设备上下文](../../mfc/device-contexts.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CPaintDC`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC MDI示例](../../top/visual-cpp-samples.md)   
 [CDC 类](../../mfc/reference/cdc-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)
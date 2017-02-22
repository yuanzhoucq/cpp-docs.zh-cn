---
title: "CClientDC Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CClientDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CClientDC class"
  - "CDC 类, device contexts for client areas"
  - "client-area device context"
  - "device contexts, 工作区"
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CClientDC Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

负责调用Windows函数 [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871) 在构造时和 [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920) 在销毁时。  
  
## 语法  
  
```  
  
class CClientDC : public CDC  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CClientDC::CClientDC](../Topic/CClientDC::CClientDC.md)|构造 `CClientDC` 对象连接到 `CWnd`。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CClientDC::m\_hWnd](../Topic/CClientDC::m_hWnd.md)|此 `CClientDC` 是有效的windows的 `HWND`。|  
  
## 备注  
 这意味着设备上下文与 `CClientDC` 对象是窗口的工作区。  
  
 有关 `CClientDC`的更多信息，请参见 [设备上下文](../../mfc/device-contexts.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CClientDC`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC MDI示例](../../top/visual-cpp-samples.md)   
 [CDC 类](../../mfc/reference/cdc-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDC 类](../../mfc/reference/cdc-class.md)
---
title: "CWindowDC Class | Microsoft Docs"
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
  - "CWindowDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWindowDC class"
  - "device contexts, 窗口"
  - "screen output classes"
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWindowDC Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从 `CDC` 派生。  
  
## 语法  
  
```  
class CWindowDC : public CDC  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CWindowDC::CWindowDC](../Topic/CWindowDC::CWindowDC.md)|构造 `CWindowDC` 对象。|  
  
### 受保护的数据成员  
  
|名称|描述|  
|--------|--------|  
|[CWindowDC::m\_hWnd](../Topic/CWindowDC::m_hWnd.md)|附加此 `CWindowDC` 的 `HWND`。|  
  
## 备注  
 在构造时调用 Windows 函数 [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947\(v=vs.85\).aspx)，在析构时调用 [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920\(v=vs.85\).aspx)。  这意味着 `CWindowDC` 对象可访问 [CWnd](../../mfc/reference/cwnd-class.md) 的整个屏幕区域（客户端和非工作区）。  
  
 有关使用 `CWindowDC` 的更多信息，请参阅[设备上下文](../../mfc/device-contexts.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CWindowDC`  
  
## 要求  
 标头: afxwin.h  
  
## 请参阅  
 [CDC 类](../../mfc/reference/cdc-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDC 类](../../mfc/reference/cdc-class.md)
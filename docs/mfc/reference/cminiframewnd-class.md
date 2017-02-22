---
title: "CMiniFrameWnd Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMiniFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMiniFrameWnd class"
  - "mini-frame windows"
  - "工具栏 [C++]"
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CMiniFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示在浮动工具栏周围通常所示的一半高度框架窗口。  
  
## 语法  
  
```  
class CMiniFrameWnd : public CFrameWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMiniFrameWnd::CMiniFrameWnd](../Topic/CMiniFrameWnd::CMiniFrameWnd.md)|构造 `CMiniFrameWnd` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMiniFrameWnd::Create](../Topic/CMiniFrameWnd::Create.md)|在构造之后创建一 `CMiniFrameWnd` 对象。|  
|[CMiniFrameWnd::CreateEx](../Topic/CMiniFrameWnd::CreateEx.md)|在构造之后创建一 `CMiniFrameWnd` 对象\(与其他选项）。|  
  
## 备注  
 这些服务器框架窗口的行为与常规框架窗口，不同之处在于，它们没有最小化和最大化按钮或菜单和必须在只关闭它们的系统菜单中单击。  
  
 若要使用 `CMiniFrameWnd` 对象，请先定义对象。  然后调用 [创建](../Topic/CMiniFrameWnd::Create.md) 成员函数显示和框架窗口。  
  
 有关如何使用 `CMiniFrameWnd` 对象的更多信息，请参见文章 [停靠的和浮动工具栏](../../mfc/docking-and-floating-toolbars.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMiniFrameWnd`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)
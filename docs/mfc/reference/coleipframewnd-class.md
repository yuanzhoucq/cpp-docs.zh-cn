---
title: "COleIPFrameWnd Class | Microsoft Docs"
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
  - "COleIPFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleIPFrameWnd class"
  - "in-place editing"
  - "OLE, 编辑"
  - "OLE, in-place activation"
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleIPFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

应用程序的就地编辑窗口的基础。  
  
## 语法  
  
```  
class COleIPFrameWnd : public CFrameWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleIPFrameWnd::COleIPFrameWnd](../Topic/COleIPFrameWnd::COleIPFrameWnd.md)|构造 `COleIPFrameWnd` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleIPFrameWnd::OnCreateControlBars](../Topic/COleIPFrameWnd::OnCreateControlBars.md)|调用由框架，该项目为就地编辑激活。|  
|[COleIPFrameWnd::RepositionFrame](../Topic/COleIPFrameWnd::RepositionFrame.md)|调用由框架重新定位就地编辑窗口。|  
  
## 备注  
 此选件类创建，并在容器应用程序内定位控件条文档窗口。  它还包含嵌入 [COleResizeBar](../../mfc/reference/coleresizebar-class.md) 对象生成的处理通知，当用户调整就地编辑窗口。  
  
 有关使用 `COleIPFrameWnd`的更多信息，请参见文章 [启动](../../mfc/activation-cpp.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `COleIPFrameWnd`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [MFC示例HIERSVR](../../top/visual-cpp-samples.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)
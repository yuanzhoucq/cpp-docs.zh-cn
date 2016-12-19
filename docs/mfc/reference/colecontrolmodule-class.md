---
title: "COleControlModule Class | Microsoft Docs"
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
  - "COleControlModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleControlModule class"
  - "control modules"
  - "MFC ActiveX controls, OLE control modules"
  - "OLE control modules"
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleControlModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从派生OLE控件模块对象的基类。  
  
## 语法  
  
```  
class COleControlModule : public CWinApp  
```  
  
## 备注  
 此选件类用于初始化控件的模块提供成员函数。  使用Microsoft基础选件类的每个OLE控件模块只能包含从 `COleControlModule`派生的对象。  在其他C\+\+全局对象构造时，此对象构造。  声明您的派生 `COleControlModule` 对象在全局级。  
  
 有关使用 `COleControlModule` 选件类的更多信息，请参见 [CWinApp](../../mfc/reference/cwinapp-class.md) 选件类和该文章 [ActiveX控件](../../mfc/mfc-activex-controls.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 `COleControlModule`  
  
## 要求  
 **Header:** afxctl.h  
  
## 请参阅  
 [MFC示例TESTHELP](../../top/visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)
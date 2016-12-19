---
title: "CHtmlEditCtrl Class | Microsoft Docs"
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
  - "CHtmlEditCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHtmlEditCtrl class"
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHtmlEditCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供webbrowser ActiveX控件的功能在MFC windows的。  
  
## 语法  
  
```  
class CHtmlEditCtrl: public CWnd,   
   public CHtmlEditCtrlBase< CHtmlEditCtrl >  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CHtmlEditCtrl::CHtmlEditCtrl](../Topic/CHtmlEditCtrl::CHtmlEditCtrl.md)|构造 `CHtmlEditCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CHtmlEditCtrl::Create](../Topic/CHtmlEditCtrl::Create.md)|创建一个浏览器ActiveX控件并将它附加到 `CHtmlEditCtrl` 对象。  此功能可自动将webbrowser ActiveX控件添加到编辑模式。|  
|[CHtmlEditCtrl::GetDHtmlDocument](../Topic/CHtmlEditCtrl::GetDHtmlDocument.md)|检索在包含的浏览器控件当前加载的文档的 [IHTMLDocument2](https://msdn.microsoft.com/en-us/library/aa752574.aspx) 接口。|  
|[CHtmlEditCtrl::GetStartDocument](../Topic/CHtmlEditCtrl::GetStartDocument.md)|在包含的浏览器控件检索URL默认文档加载。|  
  
## 备注  
 在创建后，承载的浏览器控件自动放置到编辑模式。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHtmlEditCtrl`  
  
## 要求  
 **Header:** afxhtml.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)
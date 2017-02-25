---
title: "COleCmdUI Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleCmdUI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX documents [C++], document server"
  - "COleCmdUI class"
  - "docobject server"
  - "document object server"
  - "servers [C++], ActiveX documents"
  - "servers [C++], doc objects"
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# COleCmdUI Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

执行MFC的方法可以更新用户界面对象状态与应用程序相关 `IOleCommandTarget`驱动的功能。  
  
## 语法  
  
```  
class COleCmdUI : public CCmdUI  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleCmdUI::COleCmdUI](../Topic/COleCmdUI::COleCmdUI.md)|构造 `COleCmdUI` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleCmdUI::Enable](../Topic/COleCmdUI::Enable.md)|设置或清除启用命令标志。|  
|[COleCmdUI::SetCheck](../Topic/COleCmdUI::SetCheck.md)|设置一个打开或关闭切换命令的状态。|  
|[COleCmdUI::SetText](../Topic/COleCmdUI::SetText.md)|返回命令的文本名称或状态字符串。|  
  
## 备注  
 在没有为DocObjects启用的应用程序，那么，当用户查看在应用程序中，MFC的一个菜单操作 **UPDATE\_COMMAND\_UI** notifcations。  提供可以在设计反映特定命令的状态每个通知的一 [CCmdUI](../../mfc/reference/ccmdui-class.md) 对象。  但是，那么，当您的应用程序启用对DocObjects时，MFC处理 **UPDATE\_OLE\_COMMAND\_UI** 通知并将 `COleCmdUI` 对象。  
  
 `COleCmdUI` 允许DocObject接收则源自其容器的用户界面的命令\(例如FileNew，打开，打印，等等\)，并允许容器接收则源自DocObject的用户界面的命令。  虽然 `IDispatch` 可用于计划相同的命令，`IOleCommandTarget` 提供了一种简单的方法查询，并执行，因为它依赖于标准命令，通常，不用参数和不包含类型信息是包含的。  `COleCmdUI` 可用于启用，更新和设置DocObject用户界面命令其他属性。  当要调用该命令时，请调用 [COleServerDoc::OnExecOleCmd](../Topic/COleServerDoc::OnExecOleCmd.md)。  
  
 有关DocObjects的详细信息，请参见 [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) 和 [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)。  另请参见 [Internet第一步:活动文档](../../mfc/active-documents-on-the-internet.md) 和 [活动文档](../../mfc/active-documents-on-the-internet.md)。  
  
## 继承层次结构  
 [CCmdUI](../../mfc/reference/ccmdui-class.md)  
  
 `COleCmdUI`  
  
## 要求  
 **Header:** afxdocobj.h  
  
## 请参阅  
 [CCmdUI Class](../../mfc/reference/ccmdui-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)
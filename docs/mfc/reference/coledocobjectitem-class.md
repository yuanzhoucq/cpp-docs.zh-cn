---
title: "COleDocObjectItem Class | Microsoft Docs"
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
  - "COleDocObjectItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDocObjectItem class"
  - "containment"
  - "containment, doc object"
  - "doc object containment"
  - "document object containment"
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDocObjectItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现活动文档包容。  
  
## 语法  
  
```  
class COleDocObjectItem : public COleClientItem  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleDocObjectItem::COleDocObjectItem](../Topic/COleDocObjectItem::COleDocObjectItem.md)|构造 `COleDocObject` 项目。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleDocObjectItem::DoDefaultPrinting](../Topic/COleDocObjectItem::DoDefaultPrinting.md)|使用默认打印机设置，打印容器应用程序的文档。|  
|[COleDocObjectItem::ExecCommand](../Topic/COleDocObjectItem::ExecCommand.md)|执行用户指定的命令。|  
|[COleDocObjectItem::GetActiveView](../Topic/COleDocObjectItem::GetActiveView.md)|检索文档的活动视图。|  
|[COleDocObjectItem::GetPageCount](../Topic/COleDocObjectItem::GetPageCount.md)|检索页的数量在容器应用程序的文档。|  
|[COleDocObjectItem::OnPreparePrinting](../Topic/COleDocObjectItem::OnPreparePrinting.md)|准备容器应用于打印文档。|  
|[COleDocObjectItem::OnPrint](../Topic/COleDocObjectItem::OnPrint.md)|打印容器应用程序的文档。|  
|[COleDocObjectItem::QueryCommand](../Topic/COleDocObjectItem::QueryCommand.md)|用户界面事件发生的一个或多个命令的状态的查询。|  
|[COleDocObjectItem::Release](../Topic/COleDocObjectItem::Release.md)|如果它是打开的，随OLE链接项的连接并将其关闭。  不销毁客户端项目。|  
  
## 备注  
 在MFC中，活动文档中处理类似于普通，就地编辑能嵌入，具有以下差异:  
  
-   `COleDocument`派生类仍维护当前嵌入项的列表;但是，这些项目可能是 `COleDocObjectItem`派生的项。  
  
-   在活动文档时处于活动状态，会占据视图的整个工作区，则处于就地活动状态时。  
  
-   活动文档容器包含 **Help** 菜单的完全控制。  
  
-   **Help** 菜单包含活动文档容器和服务器的菜单项。  
  
 由于活动文档容器拥有 **Help** 菜单，容器转发服务器 **Help** 菜单消息负责服务器。  此集成由 `COleDocObjectItem`处理。  
  
 有关菜单合并和激活的更多信息文档启动，请参见 [活动文档包容](../../mfc/active-document-containment.md)概述。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `COleDocObjectItem`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [MFC示例MFCBIND](../../top/visual-cpp-samples.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [CDocObjectServerItem Class](../../mfc/reference/cdocobjectserveritem-class.md)
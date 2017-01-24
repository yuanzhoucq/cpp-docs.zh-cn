---
title: "COleLinkingDoc Class | Microsoft Docs"
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
  - "COleLinkingDoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleLinkingDoc class"
  - "OLE containers, client items"
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleLinkingDoc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE容器的基类文档支持链接到嵌入项它们包含。  
  
## 语法  
  
```  
class COleLinkingDoc : public COleDocument  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleLinkingDoc::COleLinkingDoc](../Topic/COleLinkingDoc::COleLinkingDoc.md)|构造 `COleLinkingDoc` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleLinkingDoc::Register](../Topic/COleLinkingDoc::Register.md)|注册OLE系统DLL的文档。|  
|[COleLinkingDoc::Revoke](../Topic/COleLinkingDoc::Revoke.md)|移除文档中注册。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[COleLinkingDoc::OnFindEmbeddedItem](../Topic/COleLinkingDoc::OnFindEmbeddedItem.md)|查找已指定的嵌入项。|  
|[COleLinkingDoc::OnGetLinkedItem](../Topic/COleLinkingDoc::OnGetLinkedItem.md)|查找已指定的链接的项。|  
  
## 备注  
 支持连接到嵌入项的容器应用程序称为“链接容器”。[OCLIENT](../../top/visual-cpp-samples.md) 示例应用程序是链接容器的示例。  
  
 当链接项的源是在另一个了一个嵌入项文档，其中包含的文档必须加载才能编辑该嵌入项。  因此，那么，当用户编辑链接项时，的源链接容器必须能够由另一个容器应用程序生成。  您的应用程序也必须使用 [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) 选件类，以便它可以创建文档，当生成程序模型。  
  
 要使您的容器链接容器，则派生自己文档从 `COleLinkingDoc` 的选件类而不是 [COleDocument](../../mfc/reference/coledocument-class.md)。  与其他OLE容器，则必须设计您的存储应用程序的本机数据以及嵌入或链接的项目选件类。  此外，您必须将您的本机数据模型数据结构。  如果定义 `CDocItem`\-应用程序的本机数据的派生类，可以使用 `COleDocument` 定义的接口存储您的本机数据\)中的OLE数据。  
  
 若要允许应用程序由另一个容器生成程序模型，请声明 `COleTemplateServer` 对象作为应用程序的 `CWinApp`的成员派生类:  
  
 [!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/CPP/colelinkingdoc-class_1.h)]  
  
 在您的 `CWinApp`的 `InitInstance` 成员函数的派生类，请创建一个文档模板并指定您的 `COleLinkingDoc`派生类，文档选件类:  
  
 [!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/CPP/colelinkingdoc-class_2.cpp)]  
  
 连接到您的 `COleTemplateServer` 对象通过调用对象的成员函数 `ConnectTemplate` 文档模板和注册OLE系统的所有选件类对象是通过调用 **COleTemplateServer::RegisterAll**:  
  
 [!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/CPP/colelinkingdoc-class_3.cpp)]  
  
 对于样本 `CWinApp`派生类定义和 `InitInstance` 功能，请参见OCLIENT.H和OCLIENT.CPP在MFC示例 [OCLIENT](../../top/visual-cpp-samples.md)。  
  
 有关使用 `COleLinkingDoc`的更多信息，请参见位于 [容器:实现容器](../../mfc/containers-implementing-a-container.md) 和 [容器:高级功能](../../mfc/containers-advanced-features.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 `COleLinkingDoc`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [MFC示例OCLIENT](../../top/visual-cpp-samples.md)   
 [COleDocument Class](../../mfc/reference/coledocument-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)
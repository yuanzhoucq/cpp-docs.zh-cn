---
title: "活动文档包容 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "活动文档容器 [C++], 关于活动文档容器"
  - "活动文档 [C++], 容器"
  - "容器 [C++], 活动文档"
  - "MFC [C++], COM 支持"
  - "MFC COM [C++], 活动文档包容"
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 活动文档包容
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包容是活动文档提供单个帧与文档，而不是强制您创建和使用不同应用程序为每个文档类型配置的方法。  与该 OLE 的基本技术不同的 OLE 在内容仅单个可以是活动的文档中嵌入复合对象一起使用。  活动文档包容，您在单个帧的上下文内激活整个文档 \(即整个应用程序，包括关联的菜单，工具栏，等等\)。  
  
 活动文档包容技术最初开发针对 Microsoft Office 可以实现 Office 活页夹。  不过，其他 Office 和 Office 兼容应用程序外，方法是不够灵活支持的活动文档容器。Office 活页夹外，并且可支持文档服务器。  
  
 应用程序承载活动文档调用 [活动文档容器](../mfc/active-document-containers.md)。  示例这样的容器是 Microsoft Office 活页夹或 Microsoft Internet Explorer。  
  
 活动文档包容实现，即一组对 OLE 文档的扩展组合，OLE 文档技术。  扩展是一些可就地嵌入，对象表示整个文档而不是嵌入内容单个的其他接口。  带有 OLE 文档，对活动文档包容用于活动文档的显示空间中为活动文档的用户界面和功能处理的容器和服务器。  
  
 [活动文档服务器](../mfc/active-document-servers.md) 是该的应用程序 \(比如 Word、Excel、PowerPoint\) 支持一个或多个活动类文档，其中每个对象来支持中相应容器允许对象激活的扩展接口。  
  
 [活动文档](../mfc/active-documents.md) \(提供从活动文档服务器 \(如 Word 或 Excel\) 实质上是形式嵌入在另一个活动文档容器中的一个对象全部，常规文档。  与嵌入对象，对活动文档对这些页的完全控制，并且，应用程序的全部接口 \(与所有其基本命令和工具\) 提供用户编辑控件。  
  
 活动文档转换通过区分开来了解与标准 OLE 嵌入对象。  在 OLE 约定之后，嵌入对象是在文档页中显示所在的一个，并且，文档受 OLE 容器管理。  容器存储嵌入对象的数据。文档的其余部分。  但是，利用嵌入对象限制不控制它们出现的页。  
  
 活动文档容器应用程序的用户可以在创建活动文档 \(调用在 Office 活页夹的节中\) 使用用户喜爱的应用程序 \(这些应用提供程序处于活动文档\)，可以管理用户，生成的项目，在单个实体，可以唯一地命名，保存，打印，依此类推。  因此，Internet 浏览器的用户可以处理整个网络，以及本地文件系统，为单个文件存储实体能够浏览该存储的文档从一个位置。  
  
## 示例程序  
  
-   [MFCBIND](../top/visual-cpp-samples.md) 示例阐释活动文档容器应用程序的实现。  
  
## 请参阅  
 [MFC COM](../mfc/mfc-com.md)
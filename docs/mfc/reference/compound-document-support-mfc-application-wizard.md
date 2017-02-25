---
title: "MFC 应用程序向导的复合文档支持 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.exe.compdoc"
dev_langs: 
  - "C++"
ms.assetid: 42e1af83-12c4-438d-92eb-13835afdb148
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# MFC 应用程序向导的复合文档支持
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在此 MFC 应用程序向导页中，指示应用程序提供的复合文档和活动文档支持级别。  应用程序必须支持文档\/视图结构才能支持复合文档和文档模板。  
  
 默认情况下，应用程序不包含复合文档支持。  如果接受此默认值，则应用程序不能支持活动文档和复合文件。  
  
 **复合文档支持**  
 决定应用程序提供容器支持、服务器支持还是两者。  有关这方面的更多信息，请参见：  
  
-   [容器：实现容器](../../mfc/containers-implementing-a-container.md)  
  
-   [服务器：实现服务器](../../mfc/servers-implementing-a-server.md)  
  
|选项|说明|  
|--------|--------|  
|**无**|指示不支持对象链接与嵌入 \(OLE\)。  默认情况下，应用程序向导创建不带 ActiveX 支持的应用程序。|  
|**容器**|包含链接和嵌入对象。|  
|**袖珍服务器**|指示应用程序可创建和管理复合文档对象。  注意：袖珍服务器不能独立运行并且仅支持嵌入项。|  
|**完全服务器**|指示应用程序可创建和管理复合文档对象。  完全服务器能够独立运行，并且既支持链接项也支持嵌入项。|  
|**容器\/完全服务器**|指示应用程序可以既是容器又是服务器。  容器是可将嵌入项或者链接项并入自己的文档中的应用程序。  服务器是可创建供容器应用程序使用的自动化项的应用程序。|  
  
 **附加选项**  
 指示应用程序是否支持活动文档。  有关此功能的更多信息，请参见[活动文档](../../mfc/active-documents.md)。  
  
|选项|说明|  
|--------|--------|  
|**活动文档服务器**|指示应用程序可以创建和管理活动文档。  如果选择此选项，必须在向导的[文档模板字符串](../../mfc/reference/document-template-strings-mfc-application-wizard.md)页的“文件扩展名”对话框中指定活动文档服务器的文件扩展名。  有关更多信息，请参见[活动文档服务器](../../mfc/active-document-servers.md)。|  
|**活动文档容器**|指示应用程序可以在其框架中包含活动文档。  活动文档可以包含 Internet Explorer 文档或者 Office 文档（如 Microsoft Word 文件或者 Excel 电子表格）。  有关更多信息，请参见[活动文档包容](../../mfc/active-document-containment.md)。|  
|**支持复合文件**|不使用复合文件格式序列化容器应用程序的文档。  此选项强制将包含对象的整个文件加载到内存中。  个别对象的增量保存不可用。  如果更改一个对象然后保存它，则文件中的所有对象都将保存。|  
  
## 请参阅  
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)
---
title: "复合文档支持，MFC 应用程序向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.exe.compdoc
dev_langs: C++
ms.assetid: 42e1af83-12c4-438d-92eb-13835afdb148
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9390f3849cd7511054f1248205c5d2c408cb7e71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compound-document-support-mfc-application-wizard"></a>MFC 应用程序向导的复合文档支持
在 MFC 应用程序向导的此页中，指示你的应用程序提供的复合和活动文档支持级别。 你的应用程序必须支持文档/视图体系结构，以支持复合文档和文档模板。  
  
 默认情况下，应用程序包含不支持复合文档。 如果你接受此默认设置，你的应用程序不能支持活动文档或复合文件。  
  
 **复合文档支持**  
 确定你的应用程序提供容器支持和 / 或服务器支持。 有关这方面的详细信息，请参阅：  
  
-   [容器：实现容器](../../mfc/containers-implementing-a-container.md)  
  
-   [服务器：实现服务器](../../mfc/servers-implementing-a-server.md)  
  
|选项|描述|  
|------------|-----------------|  
|**无**|指示对象链接和嵌入 (OLE) 不支持。 默认情况下，应用程序向导创建一个没有 ActiveX 支持应用程序。|  
|**容器**|包含链接和嵌入对象。|  
|**袖珍服务器**|指示应用程序可以创建和管理复合文档对象。 请注意，袖珍服务器无法运行独立，并且仅支持嵌入的项。|  
|**完全服务器**|指示应用程序可以创建和管理复合文档对象。 完整的服务器都能够运行独立并且既支持链接项也支持嵌入项。|  
|**容器/完全服务器**|指示应用程序可以是一个容器和服务器。 容器是可将嵌入项或者链接项并入自己文档的应用程序。 一台服务器是可以创建自动化项以用于供容器应用程序的应用。|  
  
 **附加选项**  
 指示你的应用程序是否支持活动文档。 请参阅[活动文档](../../mfc/active-documents.md)有关此功能的详细信息。  
  
|选项|描述|  
|------------|-----------------|  
|**活动文档服务器**|指示应用程序可以创建和管理活动文档。 如果选择此选项，你必须为活动文档服务器中指定文件扩展名**文件扩展名**框中[文档模板字符串](../../mfc/reference/document-template-strings-mfc-application-wizard.md)向导页。 请参阅[活动文档服务器](../../mfc/active-document-servers.md)有关详细信息。|  
|**活动文档容器**|指示应用程序可以包含在其范围内的活动文档。 例如，活动文档可能包括 Internet Explorer 文档或 Office 文档，如 Microsoft Word 文件或 Excel 电子表格。 请参阅[活动文档包容](../../mfc/active-document-containment.md)有关详细信息。|  
|**对复合文件的支持**|不序列化使用复合文件格式的容器应用程序的文档。 此选项强制加载到内存中包含对象的整个文件。 增量存储到单个对象不可用。 如果一个对象是更改，并且随后将保存，然后保存该文件中的所有对象。|  
  
## <a name="see-also"></a>请参阅  
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)


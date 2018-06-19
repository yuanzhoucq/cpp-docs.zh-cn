---
title: 活动文档包容 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74ad16aa453c6fa0df2c84bd0a0a789b05f83169
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332668"
---
# <a name="active-document-containment"></a>活动文档包容
活动文档包容是一种技术，它提供用于处理的文档，而不是强制你创建和使用每个文档类型的多个应用程序帧中的单个帧。 它不同于基本 OLE 技术，因为 OLE 配合复合文档仅一段单独的内容可在其中活动内的嵌入对象的不同而不同。 使用活动文档包容的单个帧的上下文中激活整个文档 （即，整个应用程序，包括关联的菜单、 工具栏和等等）。  
  
 Microsoft Office，实现 Office 活页夹的最初开发的活动文档包容技术是。 但是，该技术的灵活程度足以支持 Office 活页夹以外的活动文档容器，并且可支持 Office 和 Office 兼容的应用程序以外的文档服务器。  
  
 承载活动文档的应用程序称为[活动文档容器](../mfc/active-document-containers.md)。 此类容器的示例包括 Microsoft Office Binder 或 Microsoft Internet Explorer。  
  
 根据一组扩展到 OLE 文档、 OLE 的复合文档技术实现活动文档包容。 扩展都是内容的允许的可内嵌的就地对象表示整个文档而不是内容的一段单独的嵌入的其他接口。 与 OLE 文档，活动文档包容使用活动文档和活动文档本身提供用户界面和操作的功能的服务器提供的显示空间的容器。  
  
 [活动文档服务器](../mfc/active-document-servers.md)是 （如 Word、 Excel 或 PowerPoint） 的应用程序支持一个或多个活动文档类，其中每个对象本身支持允许要在中激活的对象的扩展接口合适的容器。  
  
 [活动文档](../mfc/active-documents.md)（如 Word 或 Excel 的活动文档服务器从提供） 是实质上是一个完整规模的传统文档，将嵌入为另一个活动文档容器中的对象。 不同于嵌入对象，活动文档可以完全控制其页，并 （使用所有其基础命令和工具） 应用程序的完整界面可供用户对其进行编辑。  
  
 活动文档最区分从标准 OLE 嵌入对象被理解。 OLE 约定中，嵌入的对象是一个显示的文档的所有者，页面中，文档由 OLE 容器。 容器存储文档的其余部分使用的嵌入的对象的数据。 但是，嵌入的对象的限制在于它们不控制它们会显示的页。  
  
 活动文档容器应用程序的用户可以创建活动文档 （称为在 Office 活页夹中的部分） （前提是这些应用程序都支持活动文档） 使用他们喜欢的应用程序，但用户可以管理作为生成的项目单个实体，可以唯一地命名，保存，打印，依次类推。 相同的方式，Internet 浏览器的用户可以将整个网络，以及本地文件系统视为单个文档存储实体能够浏览该存储从一个位置中的文档。  
  
## <a name="sample-programs"></a>示例程序  
  
-   [MFCBIND](../visual-cpp-samples.md)示例阐释了活动文档容器应用程序的实现。  
  
## <a name="see-also"></a>请参阅  
 [MFC COM](../mfc/mfc-com.md)


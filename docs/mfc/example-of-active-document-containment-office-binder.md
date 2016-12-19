---
title: "活动文档包含示例：Office 活页夹 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "活动文档容器 [C++], 示例"
  - "活动文档 [C++], 容器"
  - "容器 [C++], 活动文档"
  - "示例 [C++], 活动文档包容"
  - "MFC COM [C++], 活动文档包容"
  - "Office Binder"
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 活动文档包含示例：Office 活页夹
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft Office 活页夹是活动文档容器的示例。  Office 活页夹包括主窗格，通常，容器。  左窗格包含对应于\) 将联编程序中的活动文档的图标。  每个文档调用联编程序中的 *节*。  例如，可以包含，PowerPoint 活页夹 Word 文档文件，Excel 电子表格，依此类推。  
  
 单击左侧窗格中的图标激活相应的活动文档。  联编程序的右窗格然后显示当前选择的活动文档的内容。  
  
 如果打开并激活编程序的 Word 文档时，Word 的菜单栏和工具栏将出现在视图的顶部，框架使用任何命令或 Word 工具，因此，可以编辑文档的内容。  但是，是联编程序的菜单栏和 Word 的菜单栏的组合。  由于联编程序和 Word 具有 **帮助** 菜单，单个菜单的内容合并。  活动文档容器 \(例如 Office 活页夹自动提供 **帮助** 菜单合并；有关更多信息，请参见 [帮助菜单合并](../mfc/help-menu-merging.md)。  
  
 如果选择另一个应用程序类型时活动文档，联编程序的接口更改为适应该活动文档的应用程序类型。  例如，如果包含，活页夹 Excel 电子表格，将发现编程序的菜单更改，当您选择 Excel 电子表格节。  
  
 有，当然，容器的其他可能的类型位于活页夹旁边的。  文件资源管理器使用左窗格使用的树控件显示分层目录的列表。驱动器或网络的典型、窗格界面，而右窗格显示当前选择的目录中的文件。  容器 Internet 浏览器类型 \(如 Microsoft Internet Explorer\) 可以使用超链接，而不使用双重窗格界面，通常具有单个帧并提供导航。  
  
## 请参阅  
 [活动文档包容](../mfc/active-document-containment.md)
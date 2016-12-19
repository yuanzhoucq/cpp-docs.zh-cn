---
title: "TN020：ID 命名和编号约定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.id"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "资源标识符"
  - "资源标识符, 命名和编号"
  - "TN020"
ms.assetid: aecbd2cf-68b3-47f6-ae21-b1f507917245
caps.latest.revision: 17
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN020：ID 命名和编号约定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此说明描述了MFC2.0 为资源、命令、字符串、控件和子窗口使用的ID命名和数字的约定。  
  
 MFC ID 命名和数字的约定需要满足以下要求：  
  
-   提供对Visual C\+\+资源编辑器支持的 MFC 库和 MFC 应用程序中使用的一致的 ID 命名标准。  这样对程序员就可以轻松地介绍了一种资源的类型和距其原点ID的距离。  
  
-   ID类型之间强调1对1的强关系。  
  
-   符合已经在WINDOWS中已经广泛使用的命名标准。  
  
-   分区 ID编号空间。  ID编号可由程序员、MFC、Windows、Visual C\+\+ 编辑的资源分配。  适当的分区将有助于避免ID号的副本。  
  
## ID的前缀命名规则  
 应用程序会出现集中类型的ID。  MFC ID 命名约定定义不同的资源类型有不同的前缀。  
  
 MFC 使用前缀“IDR\_”表示应用于多个资源类型的资源ID。  例如，对于特定框架窗口，则 MFC使用同一“IDR\_”前缀指示菜单、快捷键、字符串和图标资源。  下表显示各种前缀和它们的用法：  
  
|前缀|使用|  
|--------|--------|  
|IDR\_|对多个资源类型 \(主要用于菜单、快捷键和功能区\)。|  
|IDD\_|对于对话框模板资源 \(例如，IDD\_DIALOG1\)。|  
|IDC\_|对于光标资源。|  
|IDI\_|为图标资源。|  
|IDB\_|为位图资源。|  
|IDS\_|为字符串资源。|  
  
 在对话框资源中，MFC遵循以下约定：  
  
|前缀或标签|使用|  
|-----------|--------|  
|IDOK,IDCANCEL|对与标准推送按钮ID。|  
|IDC\_|对于其他对话框控件。|  
  
 “IDC\_”前缀也对游标使用。  因为典型的应用程序将有少量光标和许多对话框控件，因此命名冲突通常不是问题。  
  
 在菜单资源中，MFC遵循以下约定：  
  
|前缀|使用|  
|--------|--------|  
|IDM\_|对于菜单项不使用MFC的命令体系结构。|  
|ID\_|对于使用 MFC命令体系结构的菜单命令。|  
  
 遵守MFC命令体系的命令必须包含`ON_COMMAND`命令处理程序和`ON_UPDATE_COMMAND_UI`处理程序。  如果这些命令处理程序遵循 MFC 命令体系结构，无论他们绑定到菜单命令、工具栏按钮或对话栏按钮它们都将正常工作。  同一“ID\_”前缀也用于在程序的消息栏显示菜单提示字符串。  大多数在应用程序中的菜单项应遵循MFC 命令约定。  所有的标准命令ID\(例如, `ID_FILE_NEW`\)遵守如下约定。  
  
 MFC 还使用“IDP\_”，作为字符串的专用格式\(而不是“IDS\_”\)。  带有“IDP\_”前缀的字符串是提示，也就是说，是用于消息框的字符串。“IDP\_”字符串可以包含“%1 "和“%2 "作为有程序觉得的字符串占位符。“IDP\_”字符串通常具有与他们相关的帮助主题列表，但是，“IDS\_”字符串没有。“IDP\_”字符串始终本地化，但是“IDS\_”字符串可能不本地化。  
  
 MFC 库还使用“IDW\_”前缀，控件 ID 的专用格式\(而不是“IDC\_”\)。  这些 ID 分配给子窗口，如视图和框架选件类的拆分窗口。  MFC 以"AFX\_"前缀作为自己的实现ID。  
  
## ID编号约定  
 下表列出了特定类型的ID的有效范围。  某些限制是技术实现限制，同时，其他是旨在防止您的 ID冲突与 windows 预定义的 ID 或 MFC 默认值实现约定。  
  
 强烈建议您定义了建议的范围内的所有 ID。  范围的下限是1，因为0不能被使用。  建议您使用公共约定并使用 100 或 101 作为第一个ID.  
  
|前缀|资源类型|有效范围|  
|--------|----------|----------|  
|IDR\_|多个|1个通过0x6FFF|  
|IDD\_|对话框模板|1个通过0x6FFF|  
|IDC\_,IDI\_,IDB\_|光标，图标，位图|1个通过0x6FFF|  
|IDS\_，IDP\_|一般字符串|1 个通过0x7FFF|  
|ID\_|命令|0x8000到 0xDFFF|  
|IDC\_|控件|8个到 0xDFFF|  
  
 这些范围限制的原因  
  
-   按照约定，ID 值为 0不可用。  
  
-   窗口实现限制限制为 true 的资源 ID 小于或等于 0x7FFF。  
  
-   MFC的内部框架保留这些范围：  
  
    -   0x7000 到 0x7FFF \(请参见 afxres.h\)  
  
    -   0xE000 到0xEFFF\(请参见 afxres.h\)  
  
    -   16000 到 18000 \(请参见 afxribbonres.h\)  
  
     这些范围在将来的 MFC 实现时能更改。  
  
-   有些 windows 系统命令使用从 0xFFFF 到0xF000 的命令。  
  
-   控件ID1到7为保留的标准控件，例如 IDOK 和 IDCANCEL。  
  
-   0x8000到0xFFFF 是为字符串保留的位了菜单提示的命令。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)
---
title: "Menu Command Properties | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "menu items, properties"
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Menu Command Properties
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根据选择菜单命令时[属性窗口](../Topic/Properties%20Window.md)中出现的菜单属性组织以下信息。 按字母顺序列出属性，尽管属性窗口也使你可以按类别查看这些属性。  
  
|属性|描述|  
|--------|--------|  
|**中断**|可以是下列值之一：<br /><br /> -   **无**（默认值）：不中断。<br />-   **列**：对于静态菜单，此值将菜单命令置于新行。 对于弹出菜单，此值将菜单命令放置在新列，列之间无分隔线。 设置此属性仅会影响运行时的菜单的外观，不会影响菜单编辑器中的外观。<br />-   **栏**：与列相同，弹出菜单除外，对于弹出菜单，此值用一条竖线将新列与旧列分隔。 设置此属性仅会影响运行时的菜单的外观，不会影响菜单编辑器中的外观。|  
|**标题**|标记菜单命令（菜单名）的文本。 若要使一个菜单命令的标题中的字母之一成为助记键，请在它前面加上 & 号 \(&\)。|  
|**已选中**|如果为 True，则最初检查菜单命令。 类型：布尔型。 默认值：False。|  
|**已启用**|如果为 **False**，则菜单项被禁用。|  
|**灰显**|如果为 True，则菜单命令最初显示为灰色且处于非活动状态。 类型：布尔型。 默认值：False。|  
|**帮助**|将菜单项对齐到右侧。 例如，**帮助**菜单命令在所有 Windows 应用程序中始终位于右侧。 如果在一个菜单项上设置此属性，则该项将出现在菜单的最右边和最末尾。 适用于顶级项。 默认值：**False**。|  
|**ID**|在头文件中定义的符号。 类型：符号、整数或带引号的字符串。 你可以使用通常在任何编辑器中均可用的任何符号，即使[属性窗口](../Topic/Properties%20Window.md)不提供可供你从中进行选择的下拉列表。|  
|**弹出项**|如果为 True，则菜单命令是一个弹出菜单。 类型：布尔型。 默认值：对于菜单栏上的顶级菜单为 True；否则为 False。|  
|**提示**|包含突出显示此菜单命令时要在状态栏中显示的文本。 文本放在具有与菜单命令相同的标识符的字符串表中。 此属性可用于任何类型的项目，但运行时功能是 MFC 专用的。|  
|**从右到左对齐**|在运行时右对齐菜单栏上的菜单命令。 类型：布尔型。 默认值：False。|  
|**从右到左的顺序**|界面被本地化为任何从右到左读取的语言（例如希伯来语或阿拉伯语）时允许菜单命令按从右到左显示。|  
|**Separator**|如果为 True，则菜单命令是一个分隔符。 类型：布尔型。 默认值：False。|  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Menu Editor](../mfc/menu-editor.md)
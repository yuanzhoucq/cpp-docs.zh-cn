---
title: "菜单和资源：菜单合并 | Microsoft Docs"
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
  - "协调菜单布局"
  - "菜单 [C++], OLE 文档应用程序"
  - "合并工具栏和状态栏"
  - "OLE 容器, 菜单和资源"
  - "状态栏, OLE 文档应用程序"
  - "工具栏 [C++], OLE 文档应用程序"
  - "可视化编辑, 应用程序菜单和资源"
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 菜单和资源：菜单合并
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文详细步骤所需的 OLE 文档应用程序可以相应处理可视化编辑和就地激活。  就地激活窗体容器和服务器组件 \(\) 应用程序一个挑战。  用户在同一窗口保持在文档容器 \(帧的上下文中\)，而实际运行其他应用程序 \(服务器\)。  这要求在容器的资源和服务器应用之间的协调。  
  
 本文涵盖的主题包括：  
  
-   [菜单布局](#_core_menu_layouts)  
  
-   [工具栏和状态栏](#_core_toolbars_and_status_bars)  
  
##  <a name="_core_menu_layouts"></a> 菜单布局  
 第一步将协调菜单布局。  有关更多信息，请参见 [菜单编程的注意事项](https://msdn.microsoft.com/en-us/library/ms647557.aspx) 的 **Menu Creation** 部分 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中。  
  
 在嵌入项发生，则活动容器应用程序应使用的新菜单。  在最小值，此菜单应包括以下内容，在列出的顺序：  
  
1.  菜单为使用相同的版本文件时打开。\(其他菜单项没有在下一个项目通常前面放置。\)  
  
2.  两个连续的分隔符。  
  
3.  窗口菜单为使用相同的版本文件时打开 \(，仅在 MDI 应用程序的容器应用程序\)。  一些应用程序可能具有其他菜单，如菜单选项，本组中属于，在菜单，则嵌入的项仍存在时激活。  
  
    > [!NOTE]
    >  可能会影响文档容器的视图的其他菜单，如进行缩放。  这些容器菜单此菜单资源都会出现在两分隔符之间。  
  
 服务器组件 \(\) 应用程序还应专门创建新菜单就地激活的。  它应当与使用的菜单，当文件打开时，但没有操作，服务器文档而不是数据的菜单项，如文件和窗口。  通常，此菜单包括：  
  
1.  编辑菜单为使用相同的版本文件时打开。  
  
2.  分隔符。  
  
3.  编辑 Menu，例如 Scribble 示例应用程序的 Pen 菜单的对象。  
  
4.  分隔符。  
  
5.  “帮助”菜单  
  
 对于示例，查看某些示例就地菜单布局容器和服务器。  移除每个菜单项详细信息使示例更清晰。  容器的就地菜单中包含以下项：  
  
```  
IDR_CONTAINERTYPE_CNTR_IP MENU PRELOAD DISCARDABLE   
BEGIN  
    POPUP "&File C1"  
    MENUITEM SEPARATOR  
    POPUP "&Zoom C2"  
    MENUITEM SEPARATOR  
    POPUP "&Options C3"  
    POPUP "&Window C3"  
END  
```  
  
 连续的分隔符标记服务器的菜单的第一部分应转到。  现在请查看服务器的就地菜单：  
  
```  
IDR_SERVERTYPE_SRVR_IP MENU PRELOAD DISCARDABLE   
BEGIN  
    POPUP "&Edit S1"  
    MENUITEM SEPARATOR  
    POPUP "&Format S2"  
    MENUITEM SEPARATOR  
    POPUP "&Help S3"  
END  
```  
  
 此处分隔符标记容器菜单项的第二组应转到。  出现的菜单结构，当从该服务器的对象是用于激活的就地此容器中如下所示：  
  
```  
BEGIN  
    POPUP "&File C1"  
    POPUP "&Edit S1"  
    POPUP "&Zoom C2"  
    POPUP "&Format S2"  
    POPUP "&Options C3  
    POPUP "&Window C3"  
    POPUP "&Help S3"  
END  
```  
  
 您可以看到，分隔符为每个应用程序菜单不同的组替换。  
  
 应由服务器应用程序也提供快捷键表与就地菜单。  容器将合并到其自己的快捷键对应表中。  
  
 当嵌入项的就地激活时，框架加载就地菜单。  然后它请求其菜单的服务器应用就地激活并将其插入分隔符的位置。  这是菜单如何合并。  您从操作的菜单在容器获取文件和将窗口，因此，可以从服务器上获取操作的菜单项。  
  
##  <a name="_core_toolbars_and_status_bars"></a> 工具栏和状态栏  
 服务器应用应创建新工具栏和存储其在单独文件中的位图。  应用程序向导生成的应用程序存储在称为 ITOOLBAR.BMP 文件的该位图。  新的工具栏为容器应用程序的工具栏，当服务器上的项仍存在时激活，并应包含项和工具栏，但移除相同，对文件和 Windows 菜单项的图标。  
  
 此工具栏在 `COleIPFrameWnd`派生类加载，创建可由应用程序向导。  状态栏按容器应用程序处理。  有关就地框架窗口实现的更多信息，请参见 [服务器：实现服务器](../mfc/servers-implementing-a-server.md)。  
  
## 请参阅  
 [菜单和资源 \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [激活](../mfc/activation-cpp.md)   
 [服务器](../mfc/servers.md)   
 [容器](../mfc/containers.md)
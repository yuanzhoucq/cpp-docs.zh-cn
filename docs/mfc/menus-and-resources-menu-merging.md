---
title: "菜单和资源： 菜单合并 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c686d461a3052feb4a55cf7948b58102f10ac1f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="menus-and-resources-menu-merging"></a>菜单和资源：菜单合并
本文详细介绍 OLE 文档应用程序能够处理可视化编辑和就地激活正确所必需的步骤。 就地激活带来了挑战，容器和服务器 （组件） 应用程序。 用户保持在相同的框架窗口 （在容器文档的上下文中），但实际上正在运行另一个应用程序 （服务器）。 这要求容器和服务器应用程序的资源之间的协作。  
  
 本文中涵盖的主题包括：  
  
- [菜单布局](#_core_menu_layouts)  
  
- [工具栏和状态栏](#_core_toolbars_and_status_bars)  
  
##  <a name="_core_menu_layouts"></a>菜单布局  
 第一步是协调菜单布局。 有关详细信息，请参阅**菜单创建**主题中[菜单编程注意事项](https://msdn.microsoft.com/library/ms647557.aspx)Windows SDK 中。  
  
 容器应用程序应创建新的菜单上，仅当在就地激活嵌入的项时使用。 最小值，此菜单应包含以下内容，按列出的顺序：  
  
1.  打开文件时使用相同的文件菜单。 （通常无其他菜单项的放置位置之前的下一项。）  
  
2.  两个连续的分隔符。  
  
3.  打开文件时使用相同的窗口菜单 (仅当 MDI 应用程序中的容器应用程序)。 某些应用程序可能有属于此组中，后者在就地激活嵌入的项时仍然菜单上的其他菜单，选项菜单中，例如。  
  
    > [!NOTE]
    >  可能会影响容器的文档，如缩放的视图的其他菜单。 此菜单资源中两个分隔符之间显示这些容器菜单。  
  
 服务器 （组件） 应用程序还应创建专门用于就地激活的新菜单。 它应与菜单时文件处于打开状态，使用类似，但不具有菜单项，如文件和操作而不是数据服务器文档的窗口。 通常情况下，此菜单以下内容组成：  
  
1.  编辑菜单等同于使用打开文件时的代码。  
  
2.  分隔符。  
  
3.  编辑菜单，如钢笔菜单 Scribble 示例应用程序中的对象。  
  
4.  分隔符。  
  
5.  帮助菜单。  
  
 有关示例，请查看的一些示例的就地菜单容器和服务器布局。 已删除的每个菜单项的详细信息，若要更清晰的示例。 容器的基于就地菜单包含以下项：  
  
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
  
 连续的分隔符指示应从何处服务器的菜单的第一个部分。 现在，在服务器的基于就地菜单如下：  
  
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
  
 此处的分隔符指示应从何处容器菜单项的第二个组。 生成的菜单结构时此容器中就地激活此服务器的对象，如下所示：  
  
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
  
 如你所见，在分隔符已替换为不同组的每个应用程序的菜单。  
  
 此外应由服务器应用程序提供基于就地菜单与关联的快捷键对应表。 容器将将它们合并到其自己的快捷键对应表中。  
  
 当就地激活嵌入的项时，框架将加载基于就地菜单。 然后，在就地激活请求其菜单的服务器应用程序，并将其分隔符所在。 这是菜单的合并方式。 你的操作系统上的文件和窗口的位置，从容器获取菜单和菜单从服务器获取对该项目。  
  
##  <a name="_core_toolbars_and_status_bars"></a>工具栏和状态栏  
 服务器应用程序应创建新的工具栏，并将其位图存储在单独的文件。 应用程序向导生成应用程序将此位图存储在名为 ITOOLBAR 的文件。BMP。 在你的服务器的项到位，激活并应包含相同的项作为你正常的工具栏上，但请删除代表文件和窗口菜单上的项的图标时，新的工具栏替换容器应用程序的工具栏。  
  
 在加载此工具栏你`COleIPFrameWnd`-派生类中，为你创建应用程序向导。 由容器应用程序处理状态栏。 上的就地框架窗口的实现的详细信息，请参阅[服务器： 实现服务器](../mfc/servers-implementing-a-server.md)。  
  
## <a name="see-also"></a>请参阅  
 [菜单和资源 (OLE)](../mfc/menus-and-resources-ole.md)   
 [激活](../mfc/activation-cpp.md)   
 [服务器](../mfc/servers.md)   
 [容器](../mfc/containers.md)


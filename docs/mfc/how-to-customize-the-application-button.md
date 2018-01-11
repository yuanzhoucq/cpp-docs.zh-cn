---
title: "如何： 自定义应用程序按钮 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4a4a150985bd5c552b361620df87e34511ef8027
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-customize-the-application-button"></a>如何：自定义应用程序按钮
单击应用程序按钮时，将显示命令的菜单。 通常情况下，则菜单包含与文件相关的命令如**打开**，**保存**，**打印**，和**退出**。  
  
 ![MFC 功能区应用程序按钮](../mfc/media/application_button.png "application_button")  
  
 若要自定义应用程序按钮，打开在**属性**窗口中，修改其属性，然后预览功能区控件。  
  
### <a name="to-open-the-application-button-in-the-properties-window"></a>在属性窗口中打开的应用程序按钮  
  
1.  在 Visual Studio 中，在**视图**菜单上，单击**资源视图**。  
  
2.  在**资源视图**，双击功能区资源可将其显示在设计图面上。  
  
3.  在设计图面上，右键单击应用程序按钮菜单，然后单击**属性**。  
  
## <a name="application-button-properties"></a>应用程序按钮属性  
 下表定义的应用程序按钮的属性。  
  
|属性|定义|  
|--------------|----------------|  
|**按钮**|包含出现在应用程序菜单的右下角中的最多三个按钮的集合。|  
|**标题**|指定控件的文本。 与其他功能区元素中，不同的应用程序按钮不显示标题文本。 相反，则文本用于可访问性。|  
|**HDPI 映像**|指定的每英寸点数 (HDPI) 应用程序按钮图标的高点的标识符。 在高 DPI 显示器中，运行应用程序时**HDPI 映像**而不是使用**映像**。|  
|**HDPI 大型图像**|指定高 DPI 大型图像的标识符。 在高 DPI 显示器中，运行应用程序时**HDPI 大型图像**而不是使用**大型图像**。|  
|**HDPI 较小的图像**|指定高 DPI 较小的图像的标识符。 在高 DPI 显示器中，运行应用程序时**HDPI 小型图像**而不是使用**小型图像**。|  
|**ID**|指定控件的标识符。|  
|**Image**|指定应用程序按钮图标的标识符。 此图标为具有 alpha 透明度的 32 位 26 x 26 位图。 单击或悬停在应用程序按钮时，将突出显示的图标的透明部分。|  
|**密钥**|指定启用键提示导航后显示的字符串。 按 ALT 时启用键提示导航。|  
|**大型图像**|指定包含一系列 32x32 图标的图像的标识符。 Main 项集合中的按钮使用图标。|  
|**主要项目**|包含在应用程序菜单显示的菜单项的集合。|  
|**MRU 标题**|指定最近列表面板上显示的文本。|  
|**较小的图像**|指定包含一系列 16x16 图标的图像的标识符。 图标的按钮按钮集合中使用。|  
|**使用**|启用或禁用最近的列表面板。 在应用程序菜单上将显示最近的列表面板。|  
|**宽度**|指定以像素为单位的最新列表面板的宽度。|  
  
 应用程序菜单未出现在设计图面上。 若要查看它，您必须预览功能区或运行该应用程序。  
  
#### <a name="to-preview-the-ribbon-control"></a>预览功能区控件  
  
-   上**功能区编辑器工具栏**，单击**测试功能区**。  
  
## <a name="see-also"></a>请参阅  
 [功能区设计器 (MFC)](../mfc/ribbon-designer-mfc.md)


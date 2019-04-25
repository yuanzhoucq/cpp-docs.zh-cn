---
title: 如何：自定义应用程序按钮
ms.date: 11/19/2018
helpviewer_keywords:
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
ms.openlocfilehash: d45ceaf1cce21f77871e966e0e8f525f95cb4c37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160353"
---
# <a name="how-to-customize-the-application-button"></a>如何：自定义应用程序按钮

当单击应用程序按钮时，将显示一个菜单的命令。 通常情况下，菜单包含与文件相关的命令如**开放**，**保存**，**打印**，以及**退出**。

![MFC 功能区应用程序按钮](../mfc/media/application_button.png "MFC 功能区应用程序按钮")

若要自定义应用程序按钮，打开在**属性**窗口中，修改其属性，然后预览功能区控件。

### <a name="to-open-the-application-button-in-the-properties-window"></a>若要在属性窗口中打开的应用程序按钮

1. 在 Visual Studio 中，在**视图**菜单上，单击**资源视图**。

1. 在中**资源视图**，双击要在设计图面上显示的功能区资源。

1. 在设计图面上，右键单击应用程序按钮菜单，然后单击**属性**。

## <a name="application-button-properties"></a>应用程序按钮属性

下表定义的应用程序按钮的属性。

|属性|定义|
|--------------|----------------|
|**Button**|包含的应用程序菜单右下角出现的最多三个按钮的集合。|
|**标题**|指定控件的文本。 与其他功能区元素，不同的应用程序按钮不显示标题文本。 相反，则文本用于可访问性。|
|**HDPI Image**|指定的每英寸像素数 (HDPI) 应用程序按钮图标的标识符。 在高 DPI 显示器中，应用程序运行时**HDPI Image**而不是**映像**。|
|**HDPI Large Images**|指定高 DPI 大型映像的标识符。 在高 DPI 显示器中，应用程序运行时**HDPI Large Images**而不是**Large Images**。|
|**HDPI Small Images**|指定高 DPI 较小的图像的标识符。 在高 DPI 显示器中，应用程序运行时**HDPI Small Images**而不是**较小的图像**。|
|**ID**|指定控件的标识符。|
|**Image**|指定应用程序按钮图标的标识符。 此图标为具有 alpha 透明度的 32 位 26 x 26 位图。 单击或悬停在应用程序按钮时，将突出显示的图标的透明部分。|
|**密钥**|指定启用键提示导航时显示的字符串。 按 ALT，则启用键提示导航。|
|**大型映像**|指定包含一系列的 32x32 图标的图像的标识符。 Main Items 集合中的按钮使用的图标。|
|**主要项目**|包含应用程序菜单显示的菜单项的集合。|
|**MRU 标题**|指定最近使用列表面板上显示的文本。|
|**较小的图像**|指定包含一系列的 16x16 图标的图像的标识符。 图标按钮集合中的按钮使用。|
|**使用**|启用或禁用最近使用列表面板。 最近使用列表面板显示在应用程序菜单上。|
|**Width**|指定以像素为单位的最近使用列表面板的宽度。|

应用程序菜单不会显示在设计图面上。 若要查看它，必须预览功能区或运行该应用程序。

#### <a name="to-preview-the-ribbon-control"></a>预览功能区控件

- 上**功能区编辑器工具栏**，单击**测试功能区**。

## <a name="see-also"></a>请参阅

[功能区设计器 (MFC)](../mfc/ribbon-designer-mfc.md)

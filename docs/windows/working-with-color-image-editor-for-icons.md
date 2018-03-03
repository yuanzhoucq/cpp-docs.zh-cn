---
title: "使用颜色 （图标的图像编辑器） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.image.color
dev_langs:
- C++
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors, Image editor
- colors [C++]
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4ad0c7df6804667c3bd243668193283ecee61c8d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="working-with-color-image-editor-for-icons"></a>使用颜色（图标的图像编辑器）
图像编辑器包含很多功能，专门处理和自定义颜色。 你可以设置前景色或背景色、 限定的区域填充颜色，或选择要用作当前前景色或背景颜色的图像上的颜色。 你可以使用工具在[图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)颜色调色板中以及[颜色窗口](../windows/colors-window-image-editor-for-icons.md)来创建映像。  
  
 单色和 16 颜色映像的所有颜色调色板颜色窗口中所都示。 除了 16 种标准颜色，您可以创建您自己的自定义颜色。 更改任何调色板中的颜色将立即更改图像中相应的颜色。  
  
 当使用 256 色图标和光标映像时中的颜色属性[属性窗口](/visualstudio/ide/reference/properties-window)使用。 有关详细信息，请参阅[创建 256 色图标或光标](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)。  
  
> [!NOTE]
>  你可以使用“图像编辑器”查看 32 位图像，但是不能对它们进行编辑。  
  
 此外可以创建 true 颜色映像。 但是，true 颜色示例不显示在颜色窗口中; 在完整的调色板它们仅在前台或后台颜色指示器区域中显示。 使用创建真彩色[自定义颜色选择器对话框](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。 有关详细信息，请参阅[自定义或更改颜色](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。  
  
 你可以在磁盘上保存自定义的调色板，并根据需要重新加载这些。 最近使用的调色板保存在注册表数据并自动加载下一次启动 Visual Studio。  
  
-   [选择前景色或背景色](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)  
  
-   [填充具有一种颜色的图像的限定的区域](../windows/filling-a-bounded-area-of-an-image-with-a-color-image-editor-for-icons.md)  
  
-   [从映像用于其他地方选取颜色](../windows/picking-up-a-color-from-an-image-to-use-elsewhere-image-editor-for-icons.md)  
  
-   [选择透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)  
  
-   [反转选定内容中的颜色](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)  
  
-   [自定义或更改颜色](../windows/customizing-or-changing-colors-image-editor-for-icons.md)  
  
-   [保存和加载不同的调色板](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)  
  
-   [颜色窗口](../windows/colors-window-image-editor-for-icons.md)  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>惠?  
 无  
  
## <a name="see-also"></a>请参阅  
 [快捷键](../windows/accelerator-keys-image-editor-for-icons.md)   


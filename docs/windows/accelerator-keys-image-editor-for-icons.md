---
title: "快捷键 （图标的图像编辑器） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c992ed83f5c86fdd770bda8f9970ff98a90c2722
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="accelerator-keys-image-editor-for-icons"></a>快捷键（图标的图像编辑器）
下面是默认情况下，会将它们绑定到键的图像编辑器命令的快捷键。 若要更改快捷键，请单击**选项**上**工具**菜单，然后选择**键盘**下**环境**文件夹。 有关详细信息，请参阅[标识并自定义键盘快捷方式](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。  
  
> [!NOTE]
>  对话框中的可用选项以及显示的菜单命令的名称和位置可能与“帮助”中的描述不同，具体取决于您的当前设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅 [在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
|命令|键|描述|  
|-------------|----------|-----------------|  
|Image.AirBrushTool|CTRL + A|使用具有所选的大小和颜色的喷枪进行绘制。|  
|图像.画笔工具|CTRL + B|使用具有所选的形状、 大小和颜色的画笔绘制。|  
|Image.CopyAndOutlineSelection|CTRL + SHIFT + U|创建当前选定内容的副本并绘制其轮廓。 如果当前选定内容中包含的背景色，它将被排除在外必须[透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)选。|  
|图像.不透明处理|CTRL + J|请使当前选定内容[不透明或透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。|  
|图像.椭圆工具|CTRL + P|绘制一个具有所选的线条宽度和颜色。|  
|Image.EraserTool|CTRL + SHIFT + I|清除 （具有当前的背景色） 的映像的一部分。|  
|图像.实心椭圆工具|CTRL + SHIFT + ALT + P|绘制一个实心椭圆。|  
|图像.实心矩形工具|CTRL + SHIFT + ALT + R|绘制一个实心矩形。|  
|Image.FilledRoundRectangleTool|CTRL + SHIFT + ALT + W|绘制一个实心圆角矩形。|  
|图像.填充工具|CTRL + F|填充一块区域。|  
|图像.水平翻转|CTRL + H|水平翻转图像或选定内容。|  
|图像.垂直翻转|SHIFT + ALT + H|垂直翻转图像或选定内容。|  
|图像.较大画笔|CTRL + =|增加画笔大小（每个方向上增加一个像素）。 若要减小画笔大小，请参见本表中的“图像.较小画笔”。|  
|图像.直线工具|CTRL + L|用选定形状、大小和颜色绘制一条直线。|  
|图像.放大工具|CTRL + M|激活**放大**工具，使您得以放大图像的特定部分。|  
|图像.放大|CTRL + SHIFT + M|在当前放大倍数和 1:1 放大倍数之间切换。|  
|图像.新建图像类型|插入|将启动[新建\<设备 > 图像类型对话框](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md)使用它可以创建不同的图像类型的图像。|  
|图像.下一种颜色|CTRL +]<br /><br /> - 或 -<br /><br /> CTRL + 向右键|将绘制前景色更改为下一个调色板颜色。|  
|Image.NextRightColor|CTRL + SHIFT +]<br /><br /> - 或 -<br /><br /> SHIFT + CTRL + 向右键|将绘制背景色更改为下一个调色板颜色。|  
|图像.空心椭圆工具|SHIFT + ALT + P|用一个轮廓绘制实心椭圆。|  
|图像.空心矩形工具|SHIFT + ATL + R|用一个轮廓绘制实心矩形|  
|Image.OutlinedRoundRectangleTool|SHIFT + ALT + W|用一个轮廓绘制实心圆角矩形。|  
|图像.铅笔工具|CTRL + I|使用单像素铅笔绘制。|  
|图像.上一种颜色|CTRL + [<br /><br /> - 或 -<br /><br /> CTRL + 向的左键|将绘制前景色更改为以前的调色板颜色。|  
|Image.PreviousRightColor|CTRL + SHIFT + [<br /><br /> - 或 -<br /><br /> SHIFT + CTRL + 向的左键|将绘制背景色更改为以前的调色板颜色。|  
|图像.矩形选择工具|SHIFT + ALT + S|选择要移动、 复制或编辑的图像的矩形部分。|  
|图像.矩形工具|ATL + R|绘制一个具有所选的线条宽度和颜色的矩形。|  
|图像.旋转 90 度|CTRL + SHIFT + H|将图像或选定内容旋转 90 度。|  
|图像.圆角矩形工具|ALT + W|绘制一个具有所选的线条宽度和颜色的圆角矩形。|  
|图像.网格|CTRL + ALT + S|切换像素网格 (选择或清除**像素网格**选项[网格设置对话框](../windows/grid-settings-dialog-box-image-editor-for-icons.md))。|  
|图像.显示平铺网格|CTRL + SHIFT + ALT + S|切换磁贴网格 (选择或清除**磁贴网格**选项[网格设置对话框](../windows/grid-settings-dialog-box-image-editor-for-icons.md))。|  
|图像.小画笔|CTRL +。 （句点）|减少**画笔**大小为一个像素。 （请参见本表中的 Image.LargerBrush 和 Image.SmallerBrush。）|  
|图像.较小画笔|CTRL +-（减）|减小画笔大小（每个方向上减小一个像素）。 若要再次扩展画笔大小，请参见本表中的 Image.LargerBrush。|  
|图像.文本工具|CTRL + T|打开[文本工具对话框](../windows/text-tool-dialog-box-image-editor-for-icons.md)。|  
|Image.UseSelectionAsBrush|CTRL + U|将当前所选内容用作画笔来绘制。|  
|图像.放大|CTRL + SHIFT +。 （句点）<br /><br /> - 或 -<br /><br /> CTRL + 向上键|增加当前视图的放大倍数。|  
|图像.缩小|CTRL +，（逗号）<br /><br /> - 或 -<br /><br /> CTRL + 向下键|减小当前视图的放大倍数。|  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>惠?  
 无  
  
## <a name="see-also"></a>请参阅  
 [图标的图像编辑器](../windows/image-editor-for-icons.md)


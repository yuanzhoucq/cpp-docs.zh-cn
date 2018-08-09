---
title: 快捷键 （图标的图像编辑器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 80ab38a73a142d3ad9f80767ffe8cc8e29b0f7c6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650922"
---
# <a name="accelerator-keys-image-editor-for-icons"></a>快捷键（图标的图像编辑器）
下面是默认情况下绑定到键的图像编辑器命令的快捷键。 若要更改快捷键，请单击**选项**上**工具**菜单中，然后选择**键盘**下**环境**文件夹。 有关详细信息，请参阅[标识并自定义键盘快捷方式](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。  
  
> [!NOTE]
>  对话框中的可用选项以及显示的菜单命令的名称和位置可能与“帮助”中的描述不同，具体取决于您的当前设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
|命令|键|描述|  
|-------------|----------|-----------------|  
|Image.AirBrushTool|Ctrl + A|使用具有选定的大小和颜色的喷枪进行绘制。|  
|图像.画笔工具|**Ctrl** + **B**|使用具有选定的形状、 大小和颜色的画笔进行绘制。|  
|Image.CopyAndOutlineSelection|**Ctrl** + **Shift** + **U**|创建当前选定内容的副本并绘制其轮廓。 如果当前选定内容中包含的背景色，它将被排除在外有[透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)选定。|  
|图像.不透明处理|Ctrl + J|可以将当前选定内容[不透明或透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。|  
|图像.椭圆工具|Ctrl  +  P|绘制具有选定的线宽和颜色的椭圆。|  
|Image.EraserTool|Ctrl  +  Shift  +  I|清除 （使用当前的背景色） 的映像的一部分。|  
|图像.实心椭圆工具|**Ctrl** + **Shift** + **Alt** + **P**|绘制一个实心椭圆。|  
|图像.实心矩形工具|**Ctrl** + **Shift** + **Alt** + **R**|绘制一个实心矩形。|  
|Image.FilledRoundRectangleTool|**Ctrl** + **Shift** + **Alt** + **W**|绘制一个实心圆角矩形。|  
|图像.填充工具|Ctrl + F|填充一块区域。|  
|图像.水平翻转|Ctrl + H|水平翻转图像或选定内容。|  
|图像.垂直翻转|**Shift**+ **Alt** + **H**|垂直翻转图像或选定内容。|  
|图像.较大画笔|**Ctrl** + **=**|增加画笔大小（每个方向上增加一个像素）。 若要减小画笔大小，请参见本表中的“图像.较小画笔”。|  
|图像.直线工具|Ctrl  +  L|用选定形状、大小和颜色绘制一条直线。|  
|图像.放大工具|**Ctrl** + **M**|激活**Magnify**工具，它允许您放大你的映像的特定部分。|  
|图像.放大|Ctrl + Shift + M|在当前放大倍数和 1:1 放大倍数之间切换。|  
|图像.新建图像类型|插入|将启动[新建\<设备 > 图像类型对话框](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md)使用它创建不同的图像类型的图像。|  
|图像.下一种颜色|Ctrl + ]<br /><br /> - 或 -<br /><br /> **Ctrl** + **右箭头**|将绘制前景色更改为下一个调色板颜色。|  
|Image.NextRightColor|Ctrl + Shift + ]<br /><br /> - 或 -<br /><br /> **Shift** + **Ctrl** + **右箭头**|将绘制背景色更改为下一个调色板颜色。|  
|图像.空心椭圆工具|**Shift** + **Alt** + **P**|用一个轮廓绘制实心椭圆。|  
|图像.空心矩形工具|**Shift** + **Alt** + **R**|用一个轮廓绘制实心矩形|  
|Image.OutlinedRoundRectangleTool|**Shift** + **Alt** + **W**|用一个轮廓绘制实心圆角矩形。|  
|图像.铅笔工具|Ctrl + I|使用单像素铅笔绘制。|  
|图像.上一种颜色|Ctrl + [<br /><br /> - 或 -<br /><br /> **Ctrl** + **向左箭头**|将绘制前景色更改为以前的调色板颜色。|  
|Image.PreviousRightColor|Ctrl + Shift + [<br /><br /> - 或 -<br /><br /> **Shift** + **Ctrl** + **向左箭头**|将绘制背景色更改为以前的调色板颜色。|  
|图像.矩形选择工具|**Shift** + **Alt** + **S**|选择要移动、 复制或编辑的图像的一个矩形部分。|  
|图像.矩形工具|ATL + R|绘制一个具有选定的线宽和颜色的矩形。|  
|图像.旋转 90 度|Ctrl + Shift + H|将图像或选定内容旋转 90 度。|  
|图像.圆角矩形工具|**Alt** + **W**|绘制具有选定的线宽和颜色的圆角矩形。|  
|图像.网格|**Ctrl** + **Alt** + **S**|切换像素网格 (选择或清除**像素网格**选项[网格设置对话框](../windows/grid-settings-dialog-box-image-editor-for-icons.md))。|  
|图像.显示平铺网格|**Ctrl** + **Shift** + **Alt** + **S**|切换平铺网格 (选择或清除**平铺网格**选项[网格设置对话框](../windows/grid-settings-dialog-box-image-editor-for-icons.md))。|  
|图像.小画笔|Ctrl + . （句点）|可以减少**画笔**到一个像素大小。 （请参见本表中的 Image.LargerBrush 和 Image.SmallerBrush。）|  
|图像.较小画笔|**Ctrl**  +  **-** （减号）|减小画笔大小（每个方向上减小一个像素）。 若要再次扩展画笔大小，请参见本表中的 Image.LargerBrush。|  
|图像.文本工具|Ctrl  +  T|此时将打开[文本工具对话框](../windows/text-tool-dialog-box-image-editor-for-icons.md)。|  
|Image.UseSelectionAsBrush|**Ctrl** + **U**|将当前所选内容用作画笔来绘制。|  
|图像.放大|**Ctrl** + **Shift** + **。** （句点）<br /><br /> - 或 -<br /><br /> **Ctrl** + **向上键**|增加当前视图的放大倍数。|  
|图像.缩小|**Ctrl** + **，** （逗号）<br /><br /> - 或 -<br /><br /> **Ctrl** + **向下箭头**|减小当前视图的放大倍数。|  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 无  
  
## <a name="see-also"></a>请参阅  
 [图标的图像编辑器](../windows/image-editor-for-icons.md)
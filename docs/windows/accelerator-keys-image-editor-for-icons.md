---
title: "Accelerator Keys (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.bitmap"
  - "vc.editors.icon"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accelerator keys"
  - "Image editor [C++], accelerator keys"
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Accelerator Keys (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面是默认情况下绑定到键的图像编辑器命令的快捷键。  若要更改快捷键，请在**“工具”**菜单上单击**“选项”**，然后选择**“环境”**文件夹下的**“键盘”**。  有关更多信息，请参见[标识并自定义键盘快捷键](../Topic/Identifying%20and%20Customizing%20Keyboard%20Shortcuts%20in%20Visual%20Studio.md)。  
  
> [!NOTE]
>  对话框中的可用选项以及显示的菜单命令的名称和位置可能会与“帮助”中的描述不同，具体取决于您的现用设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关更多信息，请参见 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
|Command|键|说明|  
|-------------|-------|--------|  
|图像.喷枪工具|Ctrl \+ A|使用具有选定大小和颜色的喷枪绘制。|  
|图像.画笔工具|Ctrl \+ B|使用具有选定形状、大小和颜色的画笔绘制。|  
|图像.复制和大纲选择|Ctrl \+ Shift \+ U|创建当前选定内容的副本并绘制其轮廓。  如果背景色包含在当前选定内容中，则在您已选择[透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)的情况下它将被排除在外。|  
|图像.不透明处理|Ctrl \+ J|使当前的所选内容成为[透明或不透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。|  
|图像.椭圆工具|Ctrl \+ P|使用选定的线宽和颜色绘制一个椭圆。|  
|图像.橡皮工具|Ctrl \+ Shift \+ I|清除图像的一部分（使用当前的背景色）。|  
|图像.实心椭圆工具|Ctrl \+ Shift \+ Alt \+ P|绘制一个实心椭圆。|  
|图像.实心矩形工具|Ctrl \+ Shift \+ Alt \+ R|绘制一个实心矩形。|  
|图像.实心圆角矩形工具|Ctrl \+ Shift \+ Alt \+ W|绘制一个实心圆角矩形。|  
|图像.填充工具|Ctrl \+ F|填充一块区域。|  
|图像.水平翻转|Ctrl \+ H|水平翻转图像或选定内容。|  
|图像.垂直翻转|Shift \+ Alt \+ H|垂直翻转图像或选定内容。|  
|图像.较大画笔|Ctrl \+ \=|增加画笔大小（每个方向上增加一个像素）。  若要减小画笔大小，请参见本表中的“图像.较小画笔”。|  
|图像.直线工具|Ctrl \+ L|用选定形状、大小和颜色绘制一条直线。|  
|图像.放大工具|Ctrl \+ M|激活“放大”工具，该工具使您得以放大图像的特定部分。|  
|图像.放大|Ctrl \+ Shift \+ M|在当前放大倍数和 1:1 放大倍数之间切换。|  
|图像.新建图像类型|Insert|启动[“新建 \<设备\> 图像类型”对话框](../mfc/new-device-image-type-dialog-box-image-editor-for-icons.md)，使用它可以创建其他图像类型的图像。|  
|图像.下一种颜色|Ctrl\+\]<br /><br /> \- 或 \-<br /><br /> Ctrl \+ 向右键|将绘制前景色更改为下一个调色板颜色。|  
|Image.NextRightColor|Ctrl \+ Shift \+ \]<br /><br /> \- 或 \-<br /><br /> Shift \+ Ctrl \+ 向右键|将绘制背景色更改为下一个调色板颜色。|  
|图像.空心椭圆工具|Shift \+ Alt \+ P|用一个轮廓绘制实心椭圆。|  
|图像.空心矩形工具|Shift \+ Alt \+ R|用一个轮廓绘制实心矩形|  
|图像.圆角矩形轮廓工具|Shift \+ Alt \+ W|用一个轮廓绘制实心圆角矩形。|  
|图像.铅笔工具|Ctrl \+ I|使用单像素铅笔绘制。|  
|图像.上一种颜色|Ctrl \+ \[<br /><br /> \- 或 \-<br /><br /> Ctrl \+ 向左键|将绘制前景色更改为以前的调色板颜色。|  
|Image.PreviousRightColor|Ctrl \+ Shift \+ \[<br /><br /> \- 或 \-<br /><br /> Shift \+ Ctrl \+ 向左键|将绘制背景色更改为以前的调色板颜色。|  
|图像.矩形选择工具|Shift \+ Alt \+ S|选择图像的一个矩形部分以便移动、复制或编辑。|  
|图像.矩形工具|Alt \+ R|使用选定的线宽和颜色绘制一个矩形。|  
|图像.旋转 90 度|Ctrl \+ Shift \+ H|将图像或选定内容旋转 90 度。|  
|图像.圆角矩形工具|Alt \+ W|使用选定的线宽和颜色绘制一个圆角矩形。|  
|图像.网格|Ctrl \+ Alt \+ S|切换像素网格（选中或清除[“网格设置”对话框](../mfc/grid-settings-dialog-box-image-editor-for-icons.md)中的“像素网格”选项）。|  
|图像.显示平铺网格|Ctrl \+ Shift \+ Alt \+ S|切换平铺网格（选中或清除[“网格设置”对话框](../mfc/grid-settings-dialog-box-image-editor-for-icons.md)中的“平铺网格”选项）。|  
|图像.小画笔|Ctrl \+ .  （句点）|将**画笔**大小减小到一个像素。  （请参见本表中的 Image.LargerBrush 和 Image.SmallerBrush。）|  
|图像.较小画笔|Ctrl \+ \-（减号）|减小画笔大小（每个方向上减小一个像素）。  若要再次扩展画笔大小，请参见本表中的 Image.LargerBrush。|  
|图像.文本工具|Ctrl \+ T|打开[“文本工具”对话框](../mfc/text-tool-dialog-box-image-editor-for-icons.md)。|  
|图像.使用选择内容作为画笔|Ctrl \+ U|将当前所选内容用作画笔来绘制。|  
|图像.放大|Ctrl \+ Shift \+ .  （句点）<br /><br /> \- 或 \-<br /><br /> Ctrl \+ 向上键|增加当前视图的放大倍数。|  
|图像.缩小|Ctrl \+ ,（逗号）<br /><br /> \- 或 \-<br /><br /> Ctrl \+ 向下键|减小当前视图的放大倍数。|  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 无  
  
## 请参阅  
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)
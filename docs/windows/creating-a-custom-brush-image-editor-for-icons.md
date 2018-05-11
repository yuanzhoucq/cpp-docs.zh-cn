---
title: 创建自定义画笔 （图标的图像编辑器） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 750881aa-6f47-4de9-8ca6-a7a12afc6383
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a879850c00957568065150b6c6fc1c801c049fa2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="creating-a-custom-brush-image-editor-for-icons"></a>创建自定义画笔（图标的图像编辑器）
自定义画笔是映像的一个矩形部分的拾取和使用类似的图像编辑器的现成画笔。 你可以执行基于所选的所有操作，你可以对都执行自定义画笔。  
  
### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>若要从图像的一部分创建自定义画笔  
  
1.  [选择映像的一部分](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)想要将它用作画笔。  
  
2.  保存**SHIFT**键，单击所选内容中，在图像中拖动。  
  
     \- 或 -  
  
3.  从**映像**菜单上，选择**使用选定项作为画笔**。  
  
     你的选择将成为一个自定义画笔，它在图像中分布中所选内容的颜色。 在拖动路径也会保留所选内容的副本。 拖动时速度就越慢，进行更多副本。  
  
     **请注意**单击**所选内容用作画笔**没有首先选择部分图像将用作整个图像画笔。 使用自定义画笔的结果将还取决于是否已选择[不透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。  
  
 自定义画笔与当前的背景色匹配的像素通常是透明： 它们不绘画通过现有的映像。 可以更改此行为，以便在现有的图像上绘制背景色像素为单位。  
  
 自定义画刷一样使用戳或模具可用于创建各种特殊效果。  
  
#### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>若要绘制自定义画笔形状的背景色  
  
1.  [选择透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。  
  
2.  [设置背景色](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)到想要绘制的颜色。  
  
3.  将自定义画笔要绘制的位置。  
  
4.  单击鼠标右键按钮。 自定义画笔任何不透明区域中的背景色绘制。  
  
#### <a name="to-double-or-halve-the-custom-brush-size"></a>加倍或减半自定义画笔大小  
  
1.  按**加号**(**+**) 密钥为双精度，画笔大小，或**减号**(**-**) 键以减半.  
  
#### <a name="to-cancel-the-custom-brush"></a>若要取消的自定义画笔  
  
1.  按**ESC**或选择另一个绘制工具。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
### <a name="requirements"></a>要求  
 无  
  
## <a name="see-also"></a>请参阅  
 [快捷键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [图标的图像编辑器](../windows/image-editor-for-icons.md)


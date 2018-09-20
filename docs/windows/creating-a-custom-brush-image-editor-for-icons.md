---
title: 创建自定义画笔 （图标的图像编辑器） |Microsoft Docs
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
ms.openlocfilehash: bd4a25b208232c8a0923e33156730fc5612219a5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388194"
---
# <a name="creating-a-custom-brush-image-editor-for-icons"></a>创建自定义画笔（图标的图像编辑器）

自定义画笔是选取并的方式之一使用的图像的矩形部分**图像**编辑器的现成画笔。 可以执行所选内容的所有操作，可以自定义画笔上都执行。

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>若要从图像的一部分创建自定义画笔

1. [选择映像的一部分](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)想要将它用作画笔。

2. 持有**Shift**按键按下，单击选定内容中并在图像中拖动它。

   \- 或 -

3. 从**图像**菜单中，选择**使用所选内容用作画笔**。

   你的选择将成为在图像中分布中所选内容的颜色的自定义画笔。 在拖动路径也会保留所选内容的副本。 您拖动的速度就越慢，进行更多副本。

   > [!NOTE]
   > 单击**将所选内容用作画笔**没有首先选择图像的一部分将用作整个图像画笔。 使用自定义画笔的结果还取决于是否已选中[透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。

自定义画笔中匹配当前的背景色的像素通常是透明： 它们不在现有的图像上绘画。 可以更改此行为，以便现有图像上绘制背景色像素为单位。

如戳记或模具中的自定义画笔可用于创建各种特殊效果。

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>若要绘制自定义画笔形状中的背景色

1. [选择透明或透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。

2. [设置背景色](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)到想要绘制的颜色。

3. 定位你想要绘制的自定义画笔。

4. 单击鼠标右键。 自定义画笔的不透明的任何区域中的背景色绘制。

### <a name="to-double-or-halve-the-custom-brush-size"></a>双击或四倍的自定义画笔大小

1. 按**加号**(**+**) 密钥翻倍，画笔大小，或**减号**(**-**) 键减半.

### <a name="to-cancel-the-custom-brush"></a>若要取消的自定义画笔

1. 按**Esc**或选择另一个绘制工具。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[加速键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[图标的图像编辑器](../windows/image-editor-for-icons.md)
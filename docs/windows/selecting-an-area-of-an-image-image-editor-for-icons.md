---
title: 选择图像 （图标的图像编辑器） 的区域 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 73a773a5633ceb38173a4181e5e3effe2329fce0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419576"
---
# <a name="selecting-an-area-of-an-image-image-editor-for-icons"></a>选择图像的区域（图标的图像编辑器）

选择工具可用于定义你想要剪切、 复制、 清除、 重设大小、 反转，或移动的图像的区域。 与**矩形选择**工具可以定义并选择图像的矩形区域。 与**不规则选择**工具可以绘制需选择它以执行剪切、 复制或其他操作的区域的徒手画的轮廓。

> [!NOTE]
> 请参阅**矩形选择**并**不规则选择**工具中所示[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)或查看与的每个按钮关联的工具提示**图像编辑器**工具栏。

此外可以从选定项创建自定义画笔。 有关详细信息，请参阅[创建自定义画笔](../windows/creating-a-custom-brush-image-editor-for-icons.md)。

### <a name="to-select-an-area-of-an-image"></a>若要选择的图像的区域

1. 上**的图像编辑器**工具栏 (或从**映像**菜单中，**工具**命令)，单击你想选择的工具。

2. 将插入点移动到你想要选择的图像区域的一角。 插入点位于图像上方时，会显示十字线。

3. 到你想要选择的区域的对角拖动该插入点。 一个矩形显示了将选择的像素为单位。 所选内容中包含的矩形，包括那些在该矩形内的所有像素。

4. 释放鼠标按钮。 选择边框环绕选定的区域。

### <a name="to-select-an-entire-image"></a>若要选择整个图像

1. 单击当前所选内容之外的图像。 选择边框焦点更改，然后再一次包含整个图像。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[加速键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[图标的图像编辑器](../windows/image-editor-for-icons.md)
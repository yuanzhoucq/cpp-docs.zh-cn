---
title: 选择图像 （图标的图像编辑器） 的区域 |Microsoft 文档
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
ms.openlocfilehash: 07cb7528e25604e873f6da92193a97cf79700799
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890096"
---
# <a name="selecting-an-area-of-an-image-image-editor-for-icons"></a>选择图像的区域（图标的图像编辑器）
选择工具可用于定义你想要剪切、 复制、 清除、 调整大小、 反转，或移动图像的区域。 与**矩形选择**工具可以定义并选择图像的矩形区域。 与**不规则选择**工具可以绘制你想要选择的剪切、 复制或其他操作的区域的画概述。  
  
> [!NOTE]
>  请参阅**矩形选择**和**不规则选择**工具显示在[图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)或查看与每个按钮上关联的工具提示**图像编辑器**工具栏。  
  
 你还可以通过选择创建自定义画笔。 有关详细信息，请参阅[创建自定义画笔](../windows/creating-a-custom-brush-image-editor-for-icons.md)。  
  
### <a name="to-select-an-area-of-an-image"></a>若要选择的映像的区域  
  
1.  上**图像编辑器**工具栏 (或从**映像**菜单上，**工具**命令)，单击所需的选择工具。  
  
2.  将插入点移动到你想要选择的图像区域的一个角。 插入点位于图像上方时，会显示十字线。  
  
3.  到想要选择的区域的对角拖动该插入点。 矩形显示将选择哪些像素。 所选内容中包括的矩形，包括那些在矩形内的所有像素。  
  
4.  释放鼠标按钮。 选择边框环绕选定的区域。  
  
### <a name="to-select-an-entire-image"></a>若要选择整个图像  
  
1.  单击当前所选内容外部图像。 选择边框焦点更改，然后再一次包含整个图像。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 要求  
  
 无  
  
## <a name="see-also"></a>请参阅  
 [快捷键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [图标的图像编辑器](../windows/image-editor-for-icons.md)


---
title: 编辑图像 （图标的图像编辑器） 的部分 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
ms.assetid: ff4f5fef-71a4-4fd8-825e-049399fed391
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b33a591a2f38062b5eaf81b0f56ab73a36f4c90c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876847"
---
# <a name="editing-parts-of-an-image-image-editor-for-icons"></a>编辑图像的各个部分（图标的图像编辑器）
你可以执行标准的编辑操作-剪切、 复制、 清除和移动-上[选择](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)、 所选内容是否整个图像或它的一部分。 由于图像编辑器使用 Windows 剪贴板，你可以在图像编辑器和其他 Windows 应用程序之间传输映像。  
  
 此外，您可以调整所选内容，是否它包含整个图像或其一部分。  
  
### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>剪切当前所选内容并将它移到剪贴板  
  
1.  单击**剪切**上**编辑**菜单。  
  
### <a name="to-copy-the-selection"></a>若要复制选定内容  
  
1.  除了已调整大小控点在其上放置内选择边框或的任何位置的指针。  
  
2.  按住**CTRL**键将选择拖到新位置。 原选定内容区域保持不变。  
  
3.  若要将所选内容复制到在其当前的位置的映像，请单击选择游标外部。  
  
### <a name="to-paste-the-clipboard-contents-into-an-image"></a>若要将剪贴板内容粘贴到的映像  
  
1.  从**编辑**菜单上，选择**粘贴**。  
  
     通过选择边框，括起来的剪贴板内容显示在窗格的左上角。  
  
2.  选择边框内指针定位，并将图像拖动到所需的位置，在图像上。  
  
3.  若要定位点在其新位置的映像，请单击选择边框外部。  
  
### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>若要删除当前所选内容，而无需移动到剪贴板  
  
1.  从**编辑**菜单上，选择**删除**。  
  
     所选内容的原始区域是用当前的背景色填充的。  
  
    > [!NOTE]
    >  你可以访问剪切、 复制和粘贴，并通过在资源视图窗口中右键单击删除命令。  
  
### <a name="to-move-the-selection"></a>若要移动所选区域  
  
1.  除了已调整大小控点在其上放置内选择边框或的任何位置的指针。  
  
2.  将所选内容拖动到其新位置。  
  
3.  若要定位点在其新位置的映像中的选择，请单击选择边框外部。  
  
 通过选择的绘图的详细信息，请参阅[创建自定义画笔](../windows/creating-a-custom-brush-image-editor-for-icons.md)。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 要求  
  
 无  
  
## <a name="see-also"></a>请参阅  
 [快捷键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [图标的图像编辑器](../windows/image-editor-for-icons.md)


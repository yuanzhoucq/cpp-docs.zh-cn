---
title: 编辑图像 （图标的图像编辑器） 的各个部分 |Microsoft Docs
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
ms.openlocfilehash: 1880853c63a236e824f9b59156181dccb2bba819
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647441"
---
# <a name="editing-parts-of-an-image-image-editor-for-icons"></a>编辑图像的各个部分（图标的图像编辑器）
您可以执行标准的编辑操作 — 剪切、 复制、 清除和移动 — 上[选择](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)、 所选内容是否整个图像或它的其中一部分。 因为**图像**编辑器使用**Windows 剪贴板**，可以传输之间的映像**图像**编辑器和其他用于 Windows 应用程序。  
  
 此外，它包括整个图像或其一部分是否可以调整大小所选内容。  
  
### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>若要剪切当前所选内容并将其移动到剪贴板  
  
1.  单击**剪切**上**编辑**菜单。  
  
### <a name="to-copy-the-selection"></a>若要复制所选内容  
  
1.  除调整大小控点在其上放置内部选择边框或任意位置的指针。  
  
2.  按住**Ctrl**键将所选内容拖动到新位置。 原选定内容的区域保持不变。  
  
3.  若要将所选内容复制到其当前位置的图像，单击外部选择光标。  
  
### <a name="to-paste-the-clipboard-contents-into-an-image"></a>若要将剪贴板内容粘贴到映像中  
  
1.  从**编辑**菜单中，选择**粘贴**。  
  
     在窗格的左上角显示剪贴板内容，通过选择边框，括起来。  
  
2.  选择边框内指针定位并将图像拖到所需位置，在映像上。  
  
3.  若要定位到其新位置的映像，单击选择边框之外。  
  
### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>若要删除当前所选内容，而不将其移动到剪贴板  
  
1.  从**编辑**菜单中，选择**删除**。  
  
     使用当前的背景色填充所选内容的原始区域。  
  
    > [!NOTE]
    >  可以访问**剪切**，**副本**，**粘贴**，以及**删除**命令通过右键单击在**资源视图**窗口。  
  
### <a name="to-move-the-selection"></a>若要移动选定内容  
  
1.  除调整大小控点在其上放置内部选择边框或任意位置的指针。  
  
2.  将所选内容拖动到其新位置。  
  
3.  若要定位到其新位置的映像中的选择，单击选择边框之外。  
  
 通过选择绘图的详细信息，请参阅[创建自定义画笔](../windows/creating-a-custom-brush-image-editor-for-icons.md)。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 无  
  
## <a name="see-also"></a>请参阅  
 [加速键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [图标的图像编辑器](../windows/image-editor-for-icons.md)
---
title: 调整整个图像 （图标的图像编辑器） 的大小 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], resizing images
- size [C++], images
- images [C++], resizing
- resizing images
ms.assetid: 10782937-7eb4-4340-bdec-618ee7d7904b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2326918b6efd4c8da5f74527166d8f373dbacefc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376833"
---
# <a name="resizing-an-entire-image-image-editor-for-icons"></a>调整整个图像大小（图标的图像编辑器）

### <a name="to-resize-an-entire-image-using-the-properties-window"></a>若要调整整个图像使用属性窗口的大小

1. 打开你想要更改其属性的图像。

2. 在中**宽度**并**高度**框[属性窗口](/visualstudio/ide/reference/properties-window)，键入所需的尺寸。

   如果增大图像的大小**图像**编辑器扩展和 / 或右侧，向下，映像，并使用当前的背景色填充新的区域。 不会拉伸图像。

   如果你要减少映像的大小**图像**编辑器右边缘或下边缘，或这两者图像进行裁剪。

   > [!NOTE]
   > 可以使用**宽度**并**高度**属性，以仅整个调整图像的大小，无法调整部分选定内容的大小。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[加速键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[调整图像大小](../windows/resizing-an-image-image-editor-for-icons.md)
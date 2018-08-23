---
title: 更改图像属性 （图标的图像编辑器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- images [C++], properties
- Image editor [C++], Properties window
- Image editor [C++], image properties
- Properties window, image editor
ms.assetid: f6172bf1-08c4-4dfd-b542-dd8749e83fe6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f3c03cfa1d1d9a30cf6639b04937bacff473d7c3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604628"
---
# <a name="changing-image-properties-image-editor-for-icons"></a>更改图像属性（图标的图像编辑器）

可以设置或修改映像使用的属性[属性窗口](/visualstudio/ide/reference/properties-window)。

### <a name="to-change-an-images-properties"></a>若要更改映像的属性

1. 打开中的图像**图像**编辑器。

2. 在中**属性**窗口中，更改你的映像的任何或所有属性。

   |属性|描述|
   |--------------|-----------------|
   |**颜色**|指定图像的颜色方案。 选择**单色**， **16**，或**256**，或者**True 颜色**。 如果已绘制具有 16 调色板的图像，则选择**单色**图像会导致的黑色和白色的颜色的替换项。 对比度并不总是保持： 例如，红色和绿色的相邻区域均会转换为黑色。|
   |**文件名**|指定图像文件的名称。 默认情况下，Visual Studio 中的默认资源标识符 (IDB_BITMAP1) 并添加相应的扩展分配给通过删除前四个字符 ("IDB_") 创建的基文件名。 在此示例中的图像文件名称将为`BITMAP1.bmp`。 你可以重命名它`MYBITMAP1.bmp`。|
   |**高度**|设置图像的高度 （以像素为单位）。 默认值为 48。 裁剪图像或以下现有映像添加空格。|
   |**ID**|设置资源的标识符。 对于一个映像，Microsoft Visual Studio 中，默认情况下，将分配一系列中的下一步提供标识符： IDB_BITMAP1、 IDB_BITMAP2，依次类推。 类似的名称用于图标和光标。|
   |**调色板**|更改颜色属性。 双击以选择一种颜色，并显示[自定义颜色选择器对话框](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。 通过在相应的文本框中键入 RGB 或 HSL 值定义颜色。|
   |**SaveCompressed**|指示图像是否以压缩格式。 此属性是只读的。 Visual Studio 不允许您保存图像以压缩格式，因此，对于 Visual Studio 中创建任何图像，此属性将**False**。 如果在 Visual Studio 中打开 （在另一个程序中创建） 的压缩的映像，请将此属性 **，则返回 True**。 如果你保存压缩的映像使用 Visual Studio 中，将未压缩，并且此属性将返回到**False**。|
   |**宽度**|设置图像的宽度 （以像素为单位）。 位图的默认值为 48。 裁剪图像或空白区域添加到现有的图像的右侧。|

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[加速键](../windows/accelerator-keys-image-editor-for-icons.md)  
[编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[图标的图像编辑器](../windows/image-editor-for-icons.md)
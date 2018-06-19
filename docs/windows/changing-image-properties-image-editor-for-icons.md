---
title: 更改图像属性 （图标的图像编辑器） |Microsoft 文档
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
ms.openlocfilehash: 79903e198ddd418b96b0fac2a464dc130d81614e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863318"
---
# <a name="changing-image-properties-image-editor-for-icons"></a>更改图像属性（图标的图像编辑器）
你可以设置或修改属性的图像使用[属性窗口](/visualstudio/ide/reference/properties-window)。  
  
### <a name="to-change-an-images-properties"></a>若要更改图像属性  
  
1.  打开中的图像**映像**编辑器。  
  
2.  在**属性**窗口中，更改你的映像的任何或所有属性。  
  
    |属性|描述|  
    |--------------|-----------------|  
    |**颜色**|指定映像的配色方案。 选择单色，月 16 日，或 256，或 True 颜色。 如果您已绘制了 16 调色板的映像，选择单色图像中导致黑色和白色的颜色的替换的项。 并不总是保持对比度： 例如，红色和绿色的相邻区域均会转换为黑色。|  
    |**文件名**|指定图像文件的名称。 默认情况下，Visual Studio 将创建通过删除前四个字符 ("IDB_") 的基文件名分配从默认资源标识符 (IDB_BITMAP1) 和添加相应的扩展。 此示例中的图像的文件名称将 BITMAP1.bmp。 你无法将其重命名 MYBITMAP1.bmp。|  
    |**高度**|设置图像的高度 （以像素为单位）。 默认值为 48。 裁剪图像，或在现有图像下添加空白区域。|  
    |**ID**|设置资源的标识符。 对于一个映像，Microsoft Visual Studio 中，默认情况下，会将分配一系列中的下一步可用标识符： IDB_BITMAP1、 IDB_BITMAP2，依次类推。 类似的名称用于图标和光标。|  
    |**调色板**|更改颜色属性。 双击以选择一种颜色，然后显示[自定义颜色选择器对话框](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。 通过在相应的文本框中键入 RGB 或 HSL 值定义颜色。|  
    |**SaveCompressed**|指示映像是否以压缩格式。 此属性是只读的。 Visual Studio 不允许你保存的图像压缩格式，因此，对于 Visual Studio 中创建任何映像，此属性将是**False**。 如果你在 Visual Studio 中打开 （在另一个程序中创建） 的压缩的映像，此属性将**True**。 如果保存使用 Visual Studio 的压缩的映像，它不会进行压缩，此属性将恢复回**False**。|  
    |**宽度**|设置图像的宽度 （以像素为单位）。 位图的默认值为 48。 裁剪图像或空白区域添加到现有的图像的右侧。|  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 要求  
  
 无  
  
## <a name="see-also"></a>请参阅  
 [快捷键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [图标的图像编辑器](../windows/image-editor-for-icons.md)


---
title: 调整图像大小（图标的图像编辑器）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
- size [C++], images
- images [C++], cropping
- images [C++], extending
- Image editor [C++], cropping or extending images
- Image editor [C++], shrinking and stretching images
- images [C++], stretching
- images [C++], shrinking
- bitmaps [C++], shrinking
- bitmaps [C++], stretching
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
ms.openlocfilehash: d88a4cccff5b9b7b6303329782b7367cb953b13d
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484963"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>调整图像大小（图标的图像编辑器）

行为**图像**编辑器时调整图像的大小取决于是否已[选](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)整个图像或只是它的一部分。

所选内容包含仅的映像的一部分时**图像**编辑器通过删除行或列的像素为单位，并使用当前的背景色填充空出的区域缩小选定内容。 通过复制行或列的像素为单位，它也可以延迟所选内容。

当所选内容包括整个图像**图像**编辑器是收缩和拉伸图像，或可裁剪，并对其进行扩展。

有两种方式调整图像大小： 调整大小控点和[属性窗口](/visualstudio/ide/reference/properties-window)。 拖动调整大小控点，若要更改的所有大小或映像的一部分。 可以拖动调整大小控点都是可靠的。 您不能拖动空心的句柄。 使用**属性**窗口来调整大小整个仅，图像不是所选的一部分。

![大小调整控点上位图](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
大小调整控点

> [!NOTE]
> 如果有**磁贴网格**中选择选项[网格设置对话框](../windows/grid-settings-dialog-box-image-editor-for-icons.md)，然后调整大小将下一步的平铺网格线对齐。 如果只有**像素网格**选项是选择 （默认设置），调整大小将对齐到下一个可用的像素。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="to-resize-an-entire-image-using-the-properties-window"></a>若要调整整个图像使用属性窗口的大小

1. 打开你想要更改其属性的图像。

1. 在中**宽度**并**高度**框[属性窗口](/visualstudio/ide/reference/properties-window)，键入所需的尺寸。

   如果要增加映像的大小**图像**编辑器扩展和 / 或右侧，向下，映像，并使用当前的背景色填充新的区域。 图像未被拉伸。

   如果缩短图像的大小**图像**编辑器右边缘或下边缘，或这两者图像进行裁剪。

   > [!NOTE]
   > 可以使用**宽度**并**高度**属性，以仅整个调整图像的大小，无法调整部分选定内容的大小。

## <a name="to-crop-or-extend-an-entire-image"></a>若要裁剪或扩展整个图像

1. 选择整个图像。

   如果当前选择的映像的一部分，并且你想要选择整个图像，选择任意位置上当前选定内容边框外部图像。

1. 拖动调整大小控点，直到该图像是适当的大小。

通常情况下，**图像**编辑器裁剪或增大图像时调整其大小通过移动调整大小控点。 如果您按住**Shift**键移动大小调整句柄**映像**编辑器缩小或拉伸图像。

## <a name="to-shrink-or-stretch-an-entire-image"></a>若要缩小或拉伸整个图像

1. 选择整个图像。

   如果当前所选映像的一部分，并且你想要选择整个图像，选择任意位置上当前选定内容边框外部图像。

1. 按住**Shift**键并拖动调整大小控点，直到该图像是适当的大小。

## <a name="to-shrink-or-stretch-part-of-an-image"></a>若要缩小或拉伸图像的一部分

1. 选择要重设大小的图像的一部分。 有关详细信息，请参阅[选择的图像区域](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)。

1. 拖动调整大小控点之一，直到所选内容是适当的大小。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[快捷键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[图标的图像编辑器](../windows/image-editor-for-icons.md)
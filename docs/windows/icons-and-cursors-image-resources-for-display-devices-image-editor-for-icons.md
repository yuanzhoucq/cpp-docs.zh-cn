---
title: 图标和光标： 显示设备 （图标的图像编辑器） 的图像资源 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], creating
- image resources, display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices, creating icons for
- cursors [C++], hot spots
- icons [C++], types
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9b90337b48c46d335bfccf405b2ba7e0628b9f99
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209487"
---
# <a name="icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons"></a>图标和光标：显示设备的图像资源（图标的图像编辑器）

图标和光标是图形资源，可以为不同类型的显示设备包含大小和配色方案不同的多个图像。 此外，光标还具有一个“热点”，即 Windows 用来跟踪其位置的位置。 图标和光标使用创建和编辑**图像**编辑器中，以及位图和其他映像。

当创建新图标或光标，**图像**编辑器首先会创建标准类型的图像。 图像最初用屏幕（透明）颜色填充。 如果图像是光标，热点最初是左上角（坐标为 0,0）。

默认情况下**图像**编辑器支持为下表中所示的设备创建附加图像。 可以通过向 [自定义图像对话框](custom-image-dialog-box-image-editor-for-icons.md)中键入宽度、高度和色彩计数参数为其他设备创建图像。

> [!NOTE]
> 使用**的图像编辑器**，可以查看 32 位映像，但不能编辑这些。

|颜色|宽度（像素）|高度（像素）|
|-----------|----------------------|-----------------------|
|单色|16|16|
|单色|32|32|
|单色|48|48|
|单色|64|64|
|单色|96|96|
|16|16|16|
|16|32|32|
|16|64|64|
|16|48|48|
|16|96|96|
|256|16|16|
|256|32|32|
|256|48|48|
|256|64|64|
|256|96|96|

- [创建新设备图像（图标或光标）](../windows/creating-a-device-image-image-editor-for-icons.md)

- [为不同的显示设备添加图像](../windows/adding-an-image-for-a-different-display-device-image-editor-for-icons.md)

- [复制设备图像](../windows/copying-a-device-image-image-editor-for-icons.md)

- [删除设备图像](../windows/deleting-a-device-image-image-editor-for-icons.md)

- [在设备图像中创建透明或反转区域](../windows/creating-transparent-or-inverse-regions-in-device-images.md)

- [创建 256 色图标或光标](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)

- [设置光标的作用点](../windows/setting-a-cursor-s-hot-spot-image-editor-for-icons.md)

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[图标的图像编辑器](../windows/image-editor-for-icons.md)  
[图标](https://msdn.microsoft.com/library/windows/desktop/ms646973)  
[游标](https://msdn.microsoft.com/library/windows/desktop/ms646970)
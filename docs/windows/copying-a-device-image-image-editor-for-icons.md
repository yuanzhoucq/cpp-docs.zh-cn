---
title: 复制设备图像 （图标的图像编辑器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- display devices [C++], copying images
- cursors [C++], copying
- icons, copying
ms.assetid: 0510c20c-f820-4770-92a5-e9263a63d8be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 84e4a552f235b6ee4af8eed64017ecbb7462f032
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376897"
---
# <a name="copying-a-device-image-image-editor-for-icons"></a>复制设备图像（图标的图像编辑器）

### <a name="to-copy-a-device-image"></a>复制设备图像

1. 上**图像**菜单上，单击**打开设备图像**并从当前的图像列表中选择映像。 例如，选择 32 × 32，16 色版本的图标。

2. 复制当前显示的图标图像 (**Ctrl**+**C**)。

3. 打开另一个图像的图标在另一个**的图像编辑器**窗口。 例如，打开 16 × 16，16 色版本的图标。

4. 粘贴图标图像 (**Ctrl**+**V**) 从一个**图像编辑器**到其他窗口。 如果您要粘贴到较小的大小更大的大小，可以使用图标句柄来调整图像的大小。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[图标和光标： 显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[加速键](../windows/accelerator-keys-image-editor-for-icons.md)
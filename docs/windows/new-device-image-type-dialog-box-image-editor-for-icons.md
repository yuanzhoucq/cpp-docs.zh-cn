---
title: 新&lt;设备&gt;图像类型对话框 （c + +） （图标的图像编辑器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.newimagetype
dev_langs:
- C++
helpviewer_keywords:
- New <Device> Image Type dialog box [C++]
ms.assetid: 9c1344f5-dea0-42cd-9042-b13032f72be2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c375a10d1c8dadca643ac428422eb388c16cdae6
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313931"
---
# <a name="new-ltdevicegt-image-type-dialog-box-c-image-editor-for-icons"></a>新&lt;设备&gt;图像类型对话框 （c + +） （图标的图像编辑器）

可以创建指定类型的新设备图像。 若要打开**新建\<设备 > 图像**对话框中，单击**新建图像类型**上**映像**菜单。

### <a name="target-image-type"></a>目标图像类型

列出了可用的图像类型。 选择想要打开的映像类型：

||||
|-|-|-|
|-16 x 16，16 种颜色|-48 x 48，16 种颜色|-96 x 96，16 种颜色|
|-16 x 16，256 种颜色|-48 x 48，256 种颜色|-96 x 96，256 种颜色|
|-16 x 16，单色|-48 x 48，单色|-96 x 96，单色|
|-32 x 32，16 种颜色|-64 x 64，16 种颜色||
|-32 x 32，256 种颜色|-64 x 64，256 种颜色||
|-32 x 32，单色|-64 x 64，单色||

> [!NOTE]
> 任何现有的映像将不显示在此列表中。

### <a name="custom"></a>自定义

此时将打开[自定义映像对话框的](custom-image-dialog-box-image-editor-for-icons.md)在其中您可以创建新的映像使用自定义的大小和颜色数。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[图标和光标： 显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)  
[图像菜单](../windows/image-menu-image-editor-for-icons.md)  
[图标的图像编辑器](../windows/image-editor-for-icons.md)
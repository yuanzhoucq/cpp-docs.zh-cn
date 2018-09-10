---
title: 创建 256 色图标或光标 （图标的图像编辑器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 930a73f478b02d5aa7a16f262f98131dccba9f76
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315920"
---
# <a name="creating-a-256-color-icon-or-cursor-image-editor-for-icons"></a>创建 256 色图标或光标（图标的图像编辑器）

使用**图像**编辑器、 图标和光标可以是固定大小较大 (64 × 64) 使用 256 色调色板，可供选择。 创建资源后，选择设备映像样式。

### <a name="to-create-a-256-color-icon-or-cursor"></a>若要创建 256 色图标或光标

1. 在中[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择**插入资源**从快捷菜单。 (如果已有现有的图像资源在.rc 文件中，例如游标，只需可以右击**游标**文件夹，然后选择**插入光标**从快捷菜单。)

   > [!NOTE] 
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 在中[插入资源对话框](../windows/add-resource-dialog-box.md)，选择**图标**或**游标**然后单击**新建**。

3. 上**图像**菜单上，单击**新设备图像**。

4. 选择所需的 256 色图像样式。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[使用 256 色调色板](../windows/using-the-256-color-palette-image-editor-for-icons.md)  
[加速键](../windows/accelerator-keys-image-editor-for-icons.md)  
[图标和光标： 显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)
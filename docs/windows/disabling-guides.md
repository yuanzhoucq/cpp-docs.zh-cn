---
title: 禁用参考线 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- guides, disabling snapping
- Dialog editor, snap to guides
- snap to guides (Dialog editor)
- controls [C++], snap to guides/grid
ms.assetid: 51efa07b-8684-474e-a0b4-191ec5d91d1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9dd35bad3d7cf5a83ba25a6937ea606af81407c8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598916"
---
# <a name="disabling-guides"></a>禁用参考线

可以与鼠标一起使用的特殊键以禁用参考线的对齐效果。 使用**Alt**密钥禁用所选的指南的对齐效果。 迁移指南及**Shift**项将阻止使用该指南将移对齐的控件。

### <a name="to-disable-the-snapping-effect-of-the-guides"></a>若要禁用参考线的对齐效果

1. 此时，一直向下拖动控件**Alt**密钥。

### <a name="to-move-guides-without-moving-the-snapped-controls"></a>若要移动的参考线，而无需移动对齐的控件

1. 此时，一直向下拖动参考线**Shift**密钥。

### <a name="to-turn-off-the-guides"></a>若要关闭这些指南

1. 从**格式**菜单中，选择**参考线设置**。

2. 在中[指南设置对话框](../windows/guide-settings-dialog-box.md)下**版式参考线**，选择**None**。

   > [!NOTE]
   > 此外可以双击标尺栏以便访问**参考线设置**对话框。

\- 或 -

- 上**格式**菜单上，单击**切换辅助线**。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框编辑器状态（参考线和网格）](../windows/dialog-editor-states-guides-and-grids.md)  
[对话框中的控件](../windows/controls-in-dialog-boxes.md)
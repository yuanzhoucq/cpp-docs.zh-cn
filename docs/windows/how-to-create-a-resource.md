---
title: 如何： 创建资源 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [Visual Studio], creating
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d269dbc83c11fa4ece55d8df8f6629d1afd52c03
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594508"
---
# <a name="how-to-create-a-resource"></a>如何：创建资源

> [!NOTE]
> **资源视图**Express 版本不支持。

### <a name="to-create-a-new-resource-in-resource-view"></a>在“资源”视图中创建新资源

1. 与你的.rc 文件中的焦点[资源视图](../windows/resource-view-window.md)，单击**编辑**菜单，然后选择**添加资源**(或右键单击.rc 文件中的**资源视图** ，然后选择**添加资源**从快捷菜单)。

   > [!NOTE] 
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 在 [“添加资源”对话框](../windows/add-resource-dialog-box.md)中，选择你想要向项目中添加的资源的类型。

### <a name="to-create-a-new-resource-in-solution-explorer"></a>在解决方案资源管理器中创建新资源

1. 在 **“解决方案资源管理器”** 中，右击项目文件夹，然后选择 **“添加”**，然后单击快捷菜单上的 **“添加资源”** 。

   如果你的项目中尚无 .rc 文件，此步骤将创建一个。 然后可以重复此步骤将特定资源类型添加到新的 .rc 文件。

2. 在 [“添加资源”对话框](../windows/add-resource-dialog-box.md)中，选择你想要向项目中添加的资源的类型。

### <a name="to-create-a-new-resource-in-class-view"></a>在“类视图”中创建新资源

1. 在中[类视图](http://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，右键单击您的类，然后选择**添加**，然后单击**添加资源**从快捷菜单。

2. 在 [“添加资源”对话框](../windows/add-resource-dialog-box.md)中，选择你想要向项目中添加的资源的类型。

### <a name="to-create-a-new-resource-from-the-project-menu"></a>从“项目”菜单创建新资源

1. 从 **“项目”** 菜单中，选择 **“添加资源”**。

当创建新资源时，Visual c + + 的唯一名称为其指定，例如， `IDD_Dialog1`。 可通过在关联的资源编辑器中或 [“属性窗口”](/visualstudio/ide/reference/properties-window)中编辑该资源的属性来自定义该资源 ID。

可将资源创建为一个新的默认资源（不基于模板的资源）或采用 [模板](../windows/how-to-use-resource-templates.md)模式的资源。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源文件](../windows/resource-files-visual-studio.md)  
[资源编辑器](../windows/resource-editors.md)  
[“添加资源”对话框](../windows/add-resource-dialog-box.md)
---
title: 添加资源对话框 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.insertresource
dev_langs:
- C++
helpviewer_keywords:
- resources [C++], adding
- Add Resource dialog box [C++]
ms.assetid: e9fb6967-738f-47e8-ab58-728cf35b3af0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f44a0be0fc7614ab9dd09e814e7e444ed90e8a4a
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317662"
---
# <a name="add-resource-dialog-box"></a>“添加资源”对话框

使用此对话框将资源添加到 C++ Windows 桌面应用程序项目。

> [!NOTE]
> 此信息不适用于通用 Windows 平台应用中的资源。 有关的详细信息，请参阅[应用程序资源和资源管理系统](/windows/uwp/app-resources/)。

### <a name="resource-type"></a>资源类型

指定你想要创建的资源类型。

你可以展开光标和对话框资源目录以显示其他资源。 这些资源都位于 Visual Studio...\Microsoft `version`\VC\VCResourceTemplates\\< LCID\>\mfc.rct。 如果添加.rct 文件，必须将其放在此目录也必须指定[包括路径](../windows/how-to-specify-include-directories-for-resources.md)它们。 之后，这些文件中的资源将显示在相应类别下的第二层。 可添加的 .rct 文件数没有预设限制。

显示在树控件顶层的资源是 Visual Studio 提供的默认资源。

### <a name="new"></a>新建

创建基于的类型中选择一个资源**资源类型**框。 资源将在适当的编辑器中打开。 例如，如果创建对话框资源，它在中打开[对话框编辑器](../windows/dialog-editor.md)。

### <a name="import"></a>导入

此时将打开**导入**对话框中，在其中您可以导航到资源你想要导入到当前项目。 可导入位图、图标、光标、HTML 资源文件、声音 (.WAV) 资源文件或自定义资源文件。

### <a name="custom"></a>自定义

此时将打开[新的自定义资源对话框](../windows/new-custom-resource-dialog-box.md)在其中创建自定义资源。 仅可以在二进制编辑器中编辑自定义资源。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[如何：创建资源](../windows/how-to-create-a-resource.md)
---
title: 如何： 创建资源脚本文件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rc files, creating
- .rc files, creating
- resource script files, creating
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8b07efbd4f1434992c76de2b7e959f4578d60096
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608732"
---
# <a name="how-to-create-a-resource-script-file"></a>如何：创建资源脚本文件

> [!NOTE]
> **资源编辑器**在 Express 版本中不可用。
>
> 本材料适用于 Windows 桌面应用程序。 .NET 语言的项目不使用资源脚本文件。 有关更多信息，请参阅 [资源文件](../windows/resource-files-visual-studio.md)。

### <a name="to-create-a-new-resource-script-rc-file"></a>创建新资源脚本 (.rc) 文件

1. 将焦点放在你现有的项目文件夹**解决方案资源管理器**，例如， `MyProject`。

   > [!NOTE]
   > 不要将包含解决方案文件夹中的项目文件夹相混淆**解决方案资源管理器**。 如果将焦点放**解决方案**文件夹中中的选项**添加新项**对话框 （在步骤 3) 将不同。

2. 在 **“项目”** 菜单上，单击 **“添加新项”**。

3. 在“添加新项”  对话框中，单击 **Visual c + +** 文件夹然后选择右窗格中的“资源文件 (.rc)”  。

4. 在“名称”  文本框中为资源脚本文件命名，然后单击“打开” 。

现在可以 [创建](../windows/how-to-create-a-resource.md) 新资源并将其添加到你的 .rc 文件中。

> [!NOTE]
> 只能向加载到 Visual Studio IDE 的现有项目添加资源脚本（.rc 文件）。 不能创建独立.rc 文件（项目外的文件）。 可以随时创建[资源模板](../windows/how-to-use-resource-templates.md) （.rct 文件）。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源文件](../windows/resource-files-visual-studio.md)  
[资源编辑器](../windows/resource-editors.md)
---
title: 如何： 打开 c + + 项目 （独立版） 外的资源脚本文件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resource
dev_langs:
- C++
helpviewer_keywords:
- resources [C++], viewing
- rc files [C++], viewing resources
- .rc files [C++], viewing resources
- resource script files [C++], viewing resources
ms.assetid: bc350c60-178d-4c5d-9a7e-6576b0c936e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1e52d78de0026fa4a589877ee0a591da26107fde
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391525"
---
# <a name="how-to-open-a-resource-script-file-outside-of-a-c-project-standalone"></a>如何： 打开 c + + 项目 （独立版） 外的资源脚本文件

你可以查看 .rc 文件中的资源，而不必打开项目。 .Rc 文件将在而不是在中打开的文档窗口中打开[资源视图](../windows/resource-view-window.md)窗口 （如它在项目内打开该文件时）。

> [!NOTE]
> 这是一个重要的区别，因为仅当（在项目外部）独立打开该文件时才能显示某些命令。 例如，您可以仅保存文件以不同格式或不同的文件名称在项目外部打开该文件时 (**另存为**命令不可用时在项目内部打开一个文件)。

### <a name="to-open-an-rc-file-outside-a-project"></a>要在项目外部打开 .rc 文件

1. 从**文件**菜单中，选择**打开**，然后单击**文件**。

2. 在中**打开的文件**对话框框中，导航到资源脚本文件，你想要查看、 突出显示该文件，然后单击**打开**。

   > [!NOTE]
   > 如果您首次打开项目 (**文件**，**打开**，**项目**)，某些命令将不能给你。 “单独”打开文件意味着不先加载项目而直接打开文件。

若要打开并以文本格式查看的资源文件，请参阅[编辑资源脚本 (.rc) 文件](../windows/how-to-open-a-resource-script-file-in-text-format.md)。

### <a name="to-open-multiple-rc-files-outside-a-project"></a>若要在项目外部打开多个 .rc 文件

1. 同时单独打开这两个资源文件。 例如，打开`Source1.rc`和`Source2.rc`。

   1. 从**文件**菜单中，选择**打开**，然后单击**文件**。

   2. 在中**打开文件**对话框框中，导航到想要打开的第一个资源脚本文件 (`Source1.rc`)，突出显示该文件，然后单击**打开**。

   3. 重复上述步骤打开第二个.rc 文件 (`Source2.rc`)。

       .Rc 文件即会在单独的文档窗口中打开。

2. 当同时打开这两个 .rc 文件时，平铺窗口，以便可以同时查看它们：

   - 从**窗口**菜单中，选择**新建水平制表符组**或**新建垂直制表符组**。

       \- 或 -

   - 右键单击其中一个.rc 文件，然后选择**新建水平制表符组**或**新建垂直制表符组**从快捷菜单。

> [!NOTE]
> 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源文件](../windows/resource-files-visual-studio.md)<br/>
[资源编辑器](../windows/resource-editors.md)
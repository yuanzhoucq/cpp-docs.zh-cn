---
title: 如何： 复制资源 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
dev_langs:
- C++
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc0fc8f3177baa01742df84c926a3c6421aa9a16
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314569"
---
# <a name="how-to-copy-resources-c"></a>如何： 复制资源 （c + +）

您可以将复制资源从一个文件到另一个而不更改它们，也可以[将其复制时更改语言或资源的条件](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md)。

可以轻松地从现有的资源或可执行文件的资源复制到当前的资源文件。 若要执行此操作，您打开这两个文件同时包含资源和将项从一个文件拖动到另一种或复制并粘贴在两个文件之间。 此方法适用于资源脚本 (.rc) 文件和资源模板 (.rct) 文件，以及可执行文件 (.exe) 文件。

> [!NOTE]
> Visual c + + 包括可以在自己的应用程序中使用的示例资源文件。 有关详细信息，请参阅[剪贴画： 公共资源](https://github.com/Microsoft/VCSamples)。

你可以打开.rc 文件之间使用拖放方法[在项目外部](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。

### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>若要使用的拖放方法的文件之间复制资源

1. 打开两个独立的资源文件 (有关详细信息，请参阅[查看.rc 文件之外的项目中的资源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md))。 例如，打开 Source1.rc 和 Source2.rc。

2. 在第一个.rc 文件中，单击你想要复制的资源。 例如，在`Source1.rc`，单击**IDD_DIALOG1**。

3. 按住 CTRL 键并将资源拖到第二个.rc 文件。 例如，拖动**IDD_DIALOG1**从`Source1.rc`到`Source2.rc`。

   > [!NOTE]
   > 无需按拖动资源**Ctrl**键在移动资源，而不是复制它。

### <a name="to-copy-resources-using-copy-and-paste"></a>复制资源使用复制和粘贴

1. 打开两个独立的资源文件 (有关详细信息，请参阅[查看.rc 文件之外的项目中的资源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md))。 例如，Source1.rc 和 Source2.rc。

2. 你想要复制的资源的源文件中 (例如， `Source1.rc`)，右键单击资源，然后选择**复制**从快捷菜单。

3. 右键单击要在其中粘贴该资源的资源文件 (例如， `Source2.rc`)。 选择**粘贴**从快捷菜单。

   > [!NOTE]
   > 您不能拖放、 复制、 剪切、 或在项目中的资源文件之间粘贴 (**资源视图**) 和独立.rc 文件 （即在文档窗口中打开）。 无法在以前版本的产品来执行此操作。

   > [!NOTE]
   > 若要避免使用符号名称或现有文件中的值冲突，Visual c + + 可能会更改传输的资源的符号值或符号名称和值时将其复制到新文件。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[如何：在项目外打开资源脚本文件（独立）](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)  
[资源文件](../windows/resource-files-visual-studio.md)  
[资源编辑器](../windows/resource-editors.md)
---
title: 如何： 以文本格式 （c + +） 打开资源脚本文件 |Microsoft Docs
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
- resource script files [C++], opening in text format
- .rc files [C++], opening in text format
- rc files [C++], opening in text format
ms.assetid: 0bc57527-f53b-40c9-99a9-4dcbc5c9af57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 536448572b87da8a35ec949e0b438e0bf8f3b703
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445147"
---
# <a name="how-to-open-a-resource-script-file-in-text-format"></a>如何：以文本格式打开资源脚本文件

有时可能需要查看项目的资源脚本 (.rc) 文件的内容，而不在特定的资源编辑器中打开资源（如对话框）。 例如，可能需要在资源文件的所有对话框内搜索字符串，而不必分别打开每个对话框。

> [!NOTE]
> 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

若要查看所有包含的资源并执行全局操作支持的文本编辑器的文本格式，可以轻松打开资源文件。

> [!NOTE]
> 资源编辑器不直接读取.rc 或`resource.h`文件。 资源编译器将它们编译成由资源编辑器使用的 .aps 文件。 该文件是一个编译步骤，只存储符号数据。 与普通编译过程一样，非符号信息（如注释）在编译过程中将被放弃。 每当 .aps 文件与 .rc 文件不同步时，就会重新生成 .rc 文件（例如，当你进行“保存”时，资源编辑器将覆盖 .rc 文件和 resource.h 文件）。 对资源本身所做的任何更改依然包含在 .rc 文件中，但一旦覆盖 .rc 文件就总会丢失注释。 有关如何保留注释的信息，请参阅[编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)。

### <a name="to-open-a-resource-script-file-as-text"></a>以文本格式打开资源脚本文件

1. 从**文件**菜单中，选择**打开**，然后单击**文件。**

2. 在中**打开的文件**对话框框中，导航到你想要以文本格式查看的资源脚本文件。

3. 突出显示该文件，然后单击下拉箭头**打开**按钮 （位于按钮的右侧）。

4. 选择**打开**从下拉列表菜单。

5. 在中**打开**对话框中，单击**源代码 （文本） 编辑器**。

6. 从**打开作为**下拉列表中，选择**文本**。

   资源中打开**源代码**编辑器。

\- 或 -

1. 在中**解决方案资源管理器**，右键单击.rc 文件。

2. 从快捷菜单中，选择**打开方式...**，然后选择**源代码 （文本） 编辑器**。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源文件](../windows/resource-files-visual-studio.md)<br/>
[资源编辑器](../windows/resource-editors.md)
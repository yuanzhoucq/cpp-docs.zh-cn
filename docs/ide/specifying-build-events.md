---
title: 指定生成事件 | Microsoft Docs
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.IVCEventTool.Description
dev_langs:
- C++
helpviewer_keywords:
- Pre-Link event
- build events [C++], specifying
- custom build steps [C++], build events
- builds [C++], events
- events [C++], build
- builds [C++], customizing C++
- build events [C++]
- post-build events
ms.assetid: 788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5940f0d6efaec402a4a85ed659f42d7eab1bf91d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334959"
---
# <a name="specifying-build-events"></a>指定生成事件

可使用生成事件指定在生成开始之前、链接过程之前或生成完成之后运行的命令。

只有当生成成功到达生成过程中的这些时间点时，才执行生成事件。 如果生成中出现错误，则不会发生生成后事件；如果错误发生在链接阶段之前，则不会发生链接前和生成后事件。 此外，如果无需链接任何文件，则不会发生链接前事件。 链接前事件也不会出现在不包含链接步骤的项目中。

如果无需生成文件，则不会发生任何生成事件。

有关生成事件的一般信息，请参阅[了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)。

### <a name="to-specify-a-build-event"></a>指定生成事件

1. 在“解决方案资源管理器”中，选择要为其指定生成事件的项目。

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。

1. 在“生成事件”文件夹中，选择生成事件属性页。

1. 指定与生成事件关联的属性：

   - 在命令行中指定一个命令，就像在命令提示符处指定它一样。 指定有效的命令或批处理文件以及任何必需的输入或输出文件。 在批处理文件名称之前指定 call 批处理命令，确保执行所有后续命令。

      可使用 MSBuild 宏以符号形式指定多个输入和输出文件。 若要详细了解如何指定文件位置或文件集的名称，请参阅[用于生成命令和属性的常用宏](../ide/common-macros-for-build-commands-and-properties.md)。

      由于“%”字符已由 MSBuild 预留，如果指定环境变量，请将每个 % 转义字符替换为 %25 十六进制转义序列。 例如将 %WINDIR% 替换为 %25WINDIR%25。 MSBuild 在访问环境变量之前将每个 %25 序列替换为 % 字符。

   - 在“说明”中，键入此事件的说明。 发生此事件时，说明将打印到“输出”窗口。

   - 如果不希望运行事件，请在“从生成中排除”中指定“是”。

## <a name="see-also"></a>请参阅

[了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)  
[用于生成命令和属性的常用宏](../ide/common-macros-for-build-commands-and-properties.md)  
[生成自定义项疑难解答](../ide/troubleshooting-build-customizations.md)  

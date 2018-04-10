---
title: 指定生成事件 |Microsoft 文档
ms.custom: ''
ms.date: 12/28/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-ide
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 825eec000a2b08bd7a5a4d7769405df2f5570523
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="specifying-build-events"></a>指定生成事件

生成事件可用于指定链接过程中之前, 在生成开始之前或在生成完成之后运行的命令。

只有当生成成功到达生成过程中的这些时间点时，才执行生成事件。 如果错误发生在生成、*后期生成*事件不会发生; 如果发生此错误的链接的阶段中前, 两者*预链接*也不*后期生成*事件时发生。 此外，如果需要链接，没有文件*预链接*事件不会发生。 *预链接*事件还不是在不包含一个链接步骤的项目中可用。

如果任何文件不需要进行构建，会发生不生成事件。

生成事件的常规信息，请参阅[了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)。

### <a name="to-specify-a-build-event"></a>指定生成事件

1. 在“解决方案资源管理器”中，选择要为其指定生成事件的项目。

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。

1. 在**生成事件**文件夹中，选择生成事件属性页。

1. 指定生成事件与关联的属性：

   - 在**命令行**，指定的命令，就像已在命令提示符下指定它。 请指定有效的命令或批处理文件，任何必需的输入或输出文件。 指定**调用**批处理的批处理文件的名称前的命令，以确保执行所有后续命令。

      可以使用 MSBuild 宏以符号方式指定多个输入和输出文件。 有关如何指定的文件，位置或文件集的名称的信息，请参阅[用于生成命令和属性的公共宏](../ide/common-macros-for-build-commands-and-properties.md)。

      因为 %字符保留了 MSBuild，如果你指定的环境变量将每个 **%** 用字符转义**%25**十六进制转义序列。 例如，对于替换**%WINDIR%**与**%25WINDIR %25**。 MSBuild 替换每个**%25**序列与 **%** 字符访问环境变量之前。

   - 在**说明**，键入此事件的描述。 描述输出到**输出**窗口时将发生此事件。

   - 在**从生成中排除**，指定**是**如果你不想要运行的事件。

## <a name="see-also"></a>请参阅

[了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)  
[用于生成命令和属性的常用宏](../ide/common-macros-for-build-commands-and-properties.md)  
[生成自定义项疑难解答](../ide/troubleshooting-build-customizations.md)  

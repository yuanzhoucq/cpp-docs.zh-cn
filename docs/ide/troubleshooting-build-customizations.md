---
title: "故障排除生成自定义项 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- build events [C++], troubleshooting
- builds [C++], build events
- troubleshooting [C++], builds
- build steps [C++], troubleshooting
- events [C++], build
- builds [C++], troubleshooting
- custom build steps [C++], troubleshooting
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5fa3b2d3910a71d189f5177e13fbd91930e15ee8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="troubleshooting-build-customizations"></a>生成自定义项疑难解答
如果您的自定义生成步骤或事件没有按预期表现，，有几种方法你可以以了解发生了什么问题。  
  
-   请确保你的自定义生成步骤生成的文件匹配声明作为输出的文件。  
  
-   如果你自定义生成步骤生成的任何文件都输入或依赖关系的其他生成步骤 （自定义或其他方式），请确保这些文件将添加到你的项目。 并确保使用这些文件的工具执行后自定义生成步骤。  
  
-   若要显示自定义生成步骤实际如何操作，请添加`@echo on`作为第一个命令。 临时.bat 文件中放置和运行时生成项目时生成事件和生成步骤。 因此，你可以添加错误检查到生成事件，或生成步骤命令。  
  
-   检查以查看实际执行的内容的中间文件目录中的生成日志。 通过所表示的路径和名称生成日志**MSBuild**宏表达式**$ （intdir)\\$(MSBuildProjectName).log**。  
  
-   修改你的项目设置以收集多个默认中生成日志信息的量。 在 **“工具”** 菜单上，单击 **“选项”**。 在**选项**对话框中，单击**项目和解决方案**节点，然后单击**生成并运行**节点。 然后，在**MSBuild 项目生成日志文件详细信息**框中，单击**Detailed**。  
  
-   验证文件正在使用的名称或目录宏的任何值。 你可以单独回显宏，也可以添加`copy %0 command.bat`到自定义生成步骤开始时，请中，这将复制到 command.bat 的自定义生成步骤的命令使用所有扩展的宏。  
  
-   运行自定义生成步骤和生成事件，单独以检查它们的行为。  
  
## <a name="see-also"></a>请参阅  
 [了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)
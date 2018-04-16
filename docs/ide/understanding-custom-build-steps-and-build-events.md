---
title: "了解自定义生成步骤和生成事件 |Microsoft 文档"
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
- builds [C++], events
- custom build steps [C++], customizing builds
- events [C++], build
- custom build steps [C++]
- build steps [C++]
- build events [C++], order of events and build steps
- build steps [C++], build events
- builds [C++], custom build steps
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9abb7ff0b9a39656999e7a53b476056f7a5b1558
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-custom-build-steps-and-build-events"></a>了解自定义生成步骤和生成事件
在 Visual c + + 开发环境中，有三种基本方法来自定义生成过程：  
  
 **自定义生成步骤**  
 自定义生成步骤是与项目关联的生成规则。 自定义生成步骤可以指定命令行来执行，任何附加输入或输出文件，以及要显示的消息。 有关详细信息，请参阅[如何： 向 MSBuild 项目添加自定义生成步骤](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)。  
  
 **自定义生成工具**  
 自定义生成工具是与一个或多个文件关联的生成规则。 自定义生成步骤可将输入的文件传递给自定义生成工具，这会导致一个或多个输出文件。 例如，MFC 应用程序中的帮助文件都是用一个自定义生成工具生成的。 有关详细信息，请参阅[如何： 添加自定义生成工具向 MSBuild 项目](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)和[指定自定义生成工具](../ide/specifying-custom-build-tools.md)。  
  
 **生成事件**  
 生成事件允许你自定义项目的生成。 有三种生成事件：*预生成*，*预链接*，和*后期生成*。 生成事件，可以指定要在特定时间在生成过程中发生的操作。 例如，你可以使用生成事件注册的文件**regsvr32.exe**项目生成完成后。 有关详细信息，请参阅[指定生成事件](../ide/specifying-build-events.md)。  
  
 [故障排除生成自定义](../ide/troubleshooting-build-customizations.md)可帮助你确保自定义生成步骤，生成按预期方式运行的事件。  
  
 输出格式的自定义生成步骤或生成事件可以还可增强工具的用途。 有关详细信息，请参阅[设置自定义生成步骤或生成事件输出的格式](../ide/formatting-the-output-of-a-custom-build-step-or-build-event.md)。  
  
 生成事件和自定义生成步骤运行以及其他生成步骤顺序如下：  
  
1.  预生成事件  
  
2.  自定义生成对单独文件的工具  
  
3.  MIDL  
  
4.  资源编译器  
  
5.  C/c + + 编译器  
  
6.  Pre-Link 事件  
  
7.  链接器或库管理器 （根据需要）  
  
8.  清单工具  
  
9. BSCMake  
  
10. 项目的自定义生成步骤  
  
11. 生成后事件  
  
 `custom build step on the project`和`post-build event`运行所有其他生成后按顺序处理完成。  
  
## <a name="see-also"></a>请参阅  
 [生成 Visual Studio 中的 c + + 项目](../ide/building-cpp-projects-in-visual-studio.md)   
 [用于生成命令和属性的公共宏](../ide/common-macros-for-build-commands-and-properties.md)   
 [工具生成顺序对话框](http://msdn.microsoft.com/en-us/6204c5b1-7ce9-4948-9ff6-0268642ee14c)
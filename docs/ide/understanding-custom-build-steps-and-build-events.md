---
title: "了解自定义生成步骤和生成事件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "生成事件 [C++], 事件顺序和生成步骤"
  - "生成步骤 [C++]"
  - "生成步骤 [C++], 生成事件"
  - "builds [C++], 自定义生成步骤"
  - "builds [C++], 事件"
  - "自定义生成步骤 [C++]"
  - "自定义生成步骤 [C++], 自定义生成"
  - "事件 [C++], 生成"
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 了解自定义生成步骤和生成事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Visual C\+\+ 开发环境中，有三种自定义生成过程的基本方法：  
  
 **自定义生成步骤**  
 自定义生成步骤是与项目关联的生成规则。  自定义生成步骤可以指定要执行的命令行、任何附加输入或输出文件以及要显示的消息。  有关详细信息，请参阅[如何：向 MSBuild 项目添加自定义生成步骤](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)。  
  
 **自定义生成工具**  
 自定义生成工具是与一个或多个文件关联的生成规则。  自定义生成步骤可将输入文件传递给自定义生成工具，以生成一个或多个输出文件。  例如，MFC 应用程序中的帮助文件是用自定义生成工具生成的。  有关更多信息，请参见[如何：向 MSBuild 项目添加自定义生成工具](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)和[指定自定义生成工具](../ide/specifying-custom-build-tools.md)。  
  
 **生成事件**  
 生成事件使您可以自定义一个项目的生成。  有三种构建事件：预先生成、预链接和后期生成。  生成事件使您可以指定在生成过程中的某个特定时间要进行的操作。  例如，在项目生成完成后，可以使用生成事件用 **regsvr32.exe** 注册一个文件。  有关详细信息，请参阅[指定生成事件](../ide/specifying-build-events.md)。  
  
 [生成自定义项疑难解答](../ide/troubleshooting-build-customizations.md)可帮助您确保自定义生成步骤和生成事件如预期的那样运行。  
  
 自定义生成步骤或生成事件的输出格式还可以增强工具的可用性。  有关详细信息，请参阅[设置自定义生成步骤或生成事件输出的格式](../ide/formatting-the-output-of-a-custom-build-step-or-build-event.md)。  
  
 生成事件和自定义生成步骤与其他生成步骤一起按下列顺序运行：  
  
1.  预生成事件  
  
2.  单个文件的自定义生成工具  
  
3.  MIDL  
  
4.  资源编译器  
  
5.  C\/C\+\+ 编译器  
  
6.  预链接事件  
  
7.  链接器或管理员（根据需要）  
  
8.  清单工具  
  
9. BSCMake  
  
10. 项目的自定义生成步骤  
  
11. 生成后事件  
  
 `custom build step on the project` 和 `post-build event` 在所有其他生成进程完成之后按顺序运行。  
  
## 请参阅  
 [在 Visual Studio 中生成 C\+\+ 项目](../ide/building-cpp-projects-in-visual-studio.md)   
 [用于生成命令和属性的宏](../ide/common-macros-for-build-commands-and-properties.md)   
 [Tool Build Order Dialog Box](http://msdn.microsoft.com/zh-cn/6204c5b1-7ce9-4948-9ff6-0268642ee14c)
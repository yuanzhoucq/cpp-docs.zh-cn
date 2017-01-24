---
title: "生成自定义项疑难解答 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "生成事件 [C++], 疑难解答"
  - "生成步骤 [C++], 疑难解答"
  - "builds [C++], 生成事件"
  - "builds [C++], 疑难解答"
  - "自定义生成步骤 [C++], 疑难解答"
  - "事件 [C++], 生成"
  - "疑难解答 [C++], 生成"
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 生成自定义项疑难解答
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果自定义生成步骤或事件没有像预期的那样表现，您可以执行一些操作，以了解发生了什么问题。  
  
-   确保自定义生成步骤生成的文件与声明为输出的文件匹配。  
  
-   如果自定义生成步骤生成的任何文件是其他生成步骤（自定义或非自定义）的输入或依赖项，则确保将这些文件添加到项目中。  并确保使用那些文件的工具在自定义生成步骤之后才会执行。  
  
-   要显示自定义生成步骤实际是如何操作的，需要将 `@echo on` 添加为第一个命令。  生成事件和生成步骤都放入临时 .bat 文件中，并在生成项目时运行。  因此，您可以添加错误检查至生成事件或生成步骤命令。  
  
-   检查中间文件目录中的生成日志，查看实际执行的是什么操作。  **MSBuild** 宏表达式 **$\(IntDir\)\\$\(MSBuildProjectName\).log** 表示的内部版本记录的路径和名称。  
  
-   修改项目设置以便收集的信息量多于生成日志中的默认信息量。  在**“工具”**菜单上，单击**“选项”**。  在**“选项”**对话框中单击**“项目和解决方案”**节点，然后单击**“生成并运行”**节点。  然后在**“MSBuild 项目生成日志文件详细信息”**框中，单击**“详细”**。  
  
-   验证您正在使用的任何文件名或目录宏的值。  可以单独回显宏，或者将 `copy %0 command.bat` 添加到自定义生成步骤的开始处，该命令将自定义生成步骤的命令复制到所有宏都已展开的 command.bat 中。  
  
-   单独运行自定义生成步骤和生成事件，以检查它们的行为。  
  
## 请参阅  
 [了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)
---
title: "指定生成事件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.IVCEventTool.CommandLine"
  - "VC.Project.IVCEventTool.ExcludedFromBuild"
  - "VC.Project.IVCEventTool.Description"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "生成事件 [C++]"
  - "生成事件 [C++], 指定"
  - "builds [C++], 自定义 C++"
  - "builds [C++], 事件"
  - "自定义生成步骤 [C++], 生成事件"
  - "事件 [C++], 生成"
  - "生成后事件"
  - "Pre-Link 事件"
ms.assetid: 788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 指定生成事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用生成事件指定在生成启动前、进行链接前或生成完成后运行的命令。  
  
 只有当生成成功到达生成过程中的这些时间点时，才执行生成事件。  如果生成过程中发生错误，则不会发生生成后事件；如果错误发生在链接阶段之前，则不会发生预链接和生成后事件。  此外，如果没有要链接的文件，则不会发生预链接事件。  在不包含链接步骤的项目中，也不会有预链接事件。  
  
 如果没有要生成的文件，则不会发生生成事件。  
  
 有关生成事件的一般信息，请参见[了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)。  
  
### 指定生成事件  
  
1.  在**“解决方案资源管理器”**中，选择要为其指定生成事件的项目。  
  
2.  打开项目的**“属性页”**对话框。  有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。  
  
3.  在**“生成事件”**文件夹中，选择生成事件属性页。  
  
4.  指定与生成事件关联的属性：  
  
    -   在**“命令行”**中，指定一个命令，就像在命令提示符处指定命令一样。  指定一个有效的命令或批处理文件以及任何必需的输入或输出文件。  在批处理文件名的前面指定 **call** 批处理命令，以确保执行后面的所有命令。  
  
         可以使用 MSBuild 宏通过符号指定多个输入和输出文件。  [!INCLUDE[crabout](../build/reference/includes/crabout_md.md)]指定文件位置或文件集名称的信息，请参见[用于生成命令和属性的宏](../ide/common-macros-for-build-commands-and-properties.md)。  
  
         由于“%”字符是 MSBuild 的保留字符，因此，如果指定环境变量，请将每个 **%** 转义字符替换为 **%25** 十六进制转义序列。  例如，将 **%WINDIR%** 替换为 **%25WINDIR%25**。  在 MSBuild 访问环境变量之前，它会将每个 **%25** 序列替换为 **%** 字符。  
  
    -   在**“说明”**中，键入事件的说明。  当发生此事件时，该说明会输出到**“输出”**窗口。  
  
    -   在**“从生成中排除”**中，如果不想让事件运行，则请指定**“是”**。  
  
## 请参阅  
 [了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)   
 [用于生成命令和属性的宏](../ide/common-macros-for-build-commands-and-properties.md)   
 [生成自定义项疑难解答](../ide/troubleshooting-build-customizations.md)
---
title: "指定自定义生成工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCustomBuildTool.CustomBuildToolBeforeTargets"
  - "VC.Project.VCCustomBuildTool.Outputs"
  - "VC.Project.VCCustomBuildTool.Command"
  - "VC.Project.VCCustomBuildTool.CommandLine"
  - "VC.Project.VCCustomBuildTool.AdditionalDependencies"
  - "VC.Project.VCCustomBuildTool.Message"
  - "VC.Project.VCCustomBuildTool.CustomBuildToolAfterTargets"
  - "VC.Project.VCCustomBuildTool.Description"
  - "VC.Project.VCCustomBuildTool.AdditionalInputs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "生成工具 (C++), 指定"
  - "生成 (C++), 自定义生成工具"
  - "自定义生成工具 (C++), 指定"
ms.assetid: e5161946-8002-418d-991e-219e6a8586f5
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 指定自定义生成工具
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自定义生成工具可为生成系统提供生成特定输入文件所需的信息。  自定义生成工具指定要运行的命令、输入文件的列表、由命令生成的输出文件的列表和工具的可选说明。  
  
 有关自定义生成工具和自定义生成步骤的一般信息，请参见[了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)。  
  
### 指定自定义生成工具  
  
1.  打开项目的**“属性页”**对话框。  有关更多信息，请参见[设置 Visual C\+\+ 项目属性](../ide/working-with-project-properties.md)。  
  
2.  单击**“配置属性”**，以启用**“配置”**框。  在**“配置”**框中选择要为其指定自定义生成工具的配置。  
  
3.  在**解决方案资源管理器**中，选择自定义生成工具的输入文件。  
  
     如果没有显示**“自定义生成工具”**文件夹，则所选文件的文件扩展名与默认工具相关联。  例如，用于 .c 和 .cpp 文件的默认工具是编译器。  若要重写默认工具设置，请在**“配置属性”**节点的**“常规”**文件夹中，在**“项类型”**属性中单击**“自定义生成工具”**。  单击**“应用”**，将显示**“自定义生成工具”**节点。  
  
4.  在**“自定义生成工具”**节点的**“常规”**文件夹中，指定与自定义生成工具关联的属性：  
  
    -   在**“附加依赖项”**中，除了为自定义生成工具定义的文件以外，指定任何附加文件（与自定义生成工具关联的文件被隐式认为是该工具的输入）。  对于自定义生成工具，附加的输入文件不是必需的。  如果有一个以上的附加输入文件，可使用分号将它们分开。  
  
         如果**“附加依赖项”**文件的日期晚于输入文件的日期，则会运行自定义生成工具。  如果所有的**“附加依赖项”**文件的日期都早于输入文件的日期，而输入文件的日期早于**“输出”**属性文件的日期，则不会运行自定义生成工具。  
  
         例如，假设有一个自定义生成工具将 MyInput.x 作为输入并生成 MyInput.cpp，该 MyInput.x 包括一个头文件 MyHeader.h。  您可以指定 MyHeader.h 作为 MyInput.x 的输入依赖项，当该输入依赖项相对于 MyInput.x 或 MyHeader.h 过期时，生成系统将生成 MyInput.cpp。  
  
         输入依赖项还可以确保自定义生成工具按照所需顺序运行。  在前面的示例中，假设 MyHeader.h 实际上是自定义生成工具的输出。  因为 MyHeader.h 是 MyInput.x 的一个依赖项，所以生成系统将首先生成 Myheader.h，然后再对 MyInput.x 运行自定义生成工具。  
  
    -   在**“命令行”**中，指定一个命令，就像在命令提示符处指定命令一样。  指定一个有效的命令或批处理文件以及任何必需的输入或输出文件。  在批处理文件名的前面指定 **call** 批处理命令，以确保执行后面的所有命令。  
  
         可以使用 MSBuild 宏通过符号指定多个输入和输出文件。  [!INCLUDE[crabout](../build/reference/includes/crabout_md.md)]指定文件位置或文件集名称的信息，请参见[用于生成命令和属性的宏](../ide/common-macros-for-build-commands-and-properties.md)。  
  
         由于“%”字符是 MSBuild 的保留字符，因此，如果指定环境变量，请将每个 **%** 转义字符替换为 **%25** 十六进制转义序列。  例如，将 **%WINDIR%** 替换为 **%25WINDIR%25**。  在 MSBuild 访问环境变量之前，它会将每个 **%25** 序列替换为 **%** 字符。  
  
    -   在**“说明”**中，键入有关此自定义生成工具的描述性消息。  当生成系统处理此工具时，会将该消息输出到**“输出”**窗口中。  
  
    -   在**“输出”**中，指定输出文件的名称。  必须输入此名称；如果没有此属性的值，则自定义生成工具不会运行。  如果自定义生成工具有多个输出文件，则用分号将文件名分开。  
  
         输出文件的名称应与**“命令行”**属性中指定的名称相同。  项目生成系统将查找该文件并检查其日期。  如果输出文件比输入文件新，或未找到输出文件，则会运行自定义生成工具。  如果所有的**“附加依赖项”**文件的日期都早于输入文件的日期，而输入文件的日期早于**“输出”**属性中指定的文件的日期，则不会运行自定义生成工具。  
  
 如果要让生成系统对自定义生成工具生成的输出文件执行操作，必须手动将该文件添加到项目中。  自定义生成工具将在生成期间更新该文件。  
  
## 示例  
 假设您要在项目中包括一个名为 parser.l 的文件。  您需要一个词法分析器来处理 parser.l 以生成一个具有相同基名称的 .c 文件 \(parser.c\)。  
  
 首先，将 parser.l 和 parser.c 添加到项目中。  如果尚不存在这些文件，则只需添加对这些文件的引用。  为 parser.l 创建自定义生成工具，并在**“命令”**属性中键入以下命令：  
  
```  
lexer %(FullPath) .\%(Filename).c  
```  
  
 此命令将对 parser.l 运行词法分析器，并将 parser.c 输出到项目目录中。  
  
 在**“输出”**属性中键入：  
  
```  
.\%(Filename).c  
```  
  
 生成项目时，生成系统会比较 parser.l 和 parser.c 的时间戳。  如果 parser.l 较新或者 parser.c 不存在，则生成系统会运行**“命令行”**属性的值以更新 parser.c。  由于 parser.c 也添加到了项目中，因此，生成系统随后会编译 parser.c。  
  
## 请参阅  
 [用于生成命令和属性的宏](../ide/common-macros-for-build-commands-and-properties.md)   
 [生成自定义项疑难解答](../ide/troubleshooting-build-customizations.md)
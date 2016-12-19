---
title: "如何：向 MSBuild 项目添加自定义生成步骤 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msbuild.cpp.howto.addcustombuildstep"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (c++), 如何：添加自定义生成步骤"
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：向 MSBuild 项目添加自定义生成步骤
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自定义生成步骤是生成中用户定义的步骤。  自定义生成步骤的行为方式与任何其他命令工具步骤（如标准编译或链接工具步骤）相似。  
  
 在项目文件 \(.vcxproj\) 中指定自定义生成步骤。  此步骤可以指定要执行的命令行、任何附加输入或输出文件以及要显示的消息。  如果 **MSBuild** 确定输出文件相对于输入文件而言已过期，则它将显示该消息并执行命令。  
  
 若要指定自定义生成步骤在生成目标序列中的位置，请在项目文件中使用 `CustomBuildAfterTargets` 和 `CustomBuildBeforeTargets` XML 元素或二者之一。  例如，可以指定自定义生成步骤在链接工具目标之后且在清单工具目标之前运行。  实际的可用目标集取决于您的特定生成。  
  
 指定 `CustomBuildBeforeTargets` 元素可以在特定目标运行之前执行自定义生成步骤，指定 `CustomBuildAfterTargets` 元素可以在特定目标运行之后执行该步骤，也可以两个元素都指定以在两个相邻目标之间执行步骤。  如果未指定其中任何一个元素，则您的自定义生成工具将在其默认位置（即 **Link** 目标之后）执行。  
  
 自定义生成步骤和自定义生成工具共享在 `CustomBuildBeforeTargets` 和 `CustomBuildAfterTargets` XML 元素中指定的信息。  因此，只需在项目文件中指定一次这些目标。  
  
### 定义自定义生成步骤所执行的操作  
  
1.  将属性组添加到项目文件。  在此属性组中，指定命令、其输入和输出以及消息，如以下示例所示。  本示例将根据您在[演练：使用 MSBuild 创建 Visual C\+\+ 项目](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)中创建的 main.cpp 文件创建 .cab 文件。  
  
    ```  
    <ItemDefinitionGroup>  
      <CustomBuildStep>  
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>  
        <Outputs>$(TargetName).cab</Outputs>  
        <Inputs>$(TargetFileName)</Inputs>  
      </CustomBuildStep>  
    </ItemDefinitionGroup>  
    ```  
  
### 定义自定义生成步骤在生成中的执行位置  
  
1.  将以下属性组添加到项目文件。  您可以两个目标都指定，如果只想在特定目标之前或之后执行自定义步骤，也可以省略一个目标。  此示例通知 **MSBuild** 在编译步骤之后但在链接步骤之前执行自定义步骤。  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## 请参阅  
 [演练：使用 MSBuild 创建 Visual C\+\+ 项目](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [如何：在 MSBuild 项目中使用生成事件](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [如何：向 MSBuild 项目添加自定义生成工具](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)
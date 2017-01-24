---
title: "如何：向 MSBuild 项目添加自定义生成工具 | Microsoft Docs"
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
  - "msbuild.cpp.howto.addcustombuildtools"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (c++), 如何：添加自定义生成工具"
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：向 MSBuild 项目添加自定义生成工具
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自定义生成工具是与特定文件关联的用户定义的命令行工具。  
  
 对于特定文件，请在项目文件 \(.vcxproj\) 中指定要执行的命令行、任何附加输入或输出文件以及要显示的消息。  如果 **MSBuild** 确定输出文件相对于输入文件而言已过期，则它将显示该消息并执行命令行工具。  
  
 若要指定自定义生成工具的执行时间，请在项目文件中使用 `CustomBuildBeforeTargets` 和 `CustomBuildAfterTargets` XML 元素或二者之一。  例如，可以指定自定义生成工具在 MIDL 编译器之后但在 C\/C\+\+ 编译器之前运行。  指定 `CustomBuildBeforeTargets` 元素可以在特定目标运行之前执行该工具，指定 `CustomBuildAfterTargets` 元素可以在特定目标运行之后执行该工具，也可以两个元素都指定以在两个目标的执行过程之间运行该工具。  如果未指定其中任何一个元素，则您的自定义生成工具将在其默认位置（即 **MIDL** 目标之前）执行。  
  
 自定义生成步骤和自定义生成工具共享在 `CustomBuildBeforeTargets` 和 `CustomBuildAfterTargets` XML 元素中指定的信息。  请在项目文件中指定一次这些目标。  
  
### 添加自定义生成工具  
  
1.  将项目组添加到项目文件中，并为每个输入文件添加项。  将命令、附加输入、输出和消息指定为项元数据，如此处所示。  此示例假定“faq.txt”文件与项目在同一目录中。  
  
    ```  
    <ItemGroup>  
      <CustomBuild Include="faq.txt">  
        <Message>Copying readme...</Message>  
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>  
        <Outputs>$(OutDir)%(Identity)</Outputs>  
      </CustomBuild>  
    </ItemGroup>  
    ```  
  
### 定义自定义生成工具在生成中的执行位置  
  
1.  将以下属性组添加到项目文件。  您至少必须指定一个目标，但是如果只想在特定目标之前（或之后）执行生成步骤，则可以省略另一个目标。  此示例在编译之后但在链接之前执行自定义步骤。  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## 请参阅  
 [演练：使用 MSBuild 创建 Visual C\+\+ 项目](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [如何：在 MSBuild 项目中使用生成事件](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [如何：向 MSBuild 项目添加自定义生成步骤](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)
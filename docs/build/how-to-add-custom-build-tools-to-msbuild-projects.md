---
title: 如何： 向 MSBuild 项目添加自定义生成工具 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msbuild.cpp.howto.addcustombuildtools
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efa484e4ad57a3a1f27621e16dddcf90135b7057
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>如何：向 MSBuild 项目添加自定义生成工具
自定义生成工具是与特定的文件关联的用户定义的命令行工具。  
  
 对于特定的文件，请指定要执行的项目文件 (.vcxproj) 命令行、 任何其他输入或输出文件和要显示的消息中。 如果**MSBuild**确定输出文件已与你输入的文件过期，则它将显示的消息并执行命令行工具。  
  
 若要指定自定义生成工具的执行时，使用一个或两个`CustomBuildBeforeTargets`和`CustomBuildAfterTargets`项目文件中的 XML 元素。 例如，你可能指定自定义生成工具运行之后 MIDL 编译器和 C/c + + 编译器之前。 指定`CustomBuildBeforeTargets`元素特定目标运行; 之前执行该工具`CustomBuildAfterTargets`在特定的目标; 之后执行该工具的元素或这两个元素的两个目标执行之间运行该工具。 如果指定两个元素中，则将在其默认位置，这就是之前执行自定义生成工具**MIDL**目标。  
  
 自定义生成步骤和自定义生成工具共享中指定的信息`CustomBuildBeforeTargets`和`CustomBuildAfterTargets`XML 元素。 在你的项目文件中指定这些目标一次。  
  
### <a name="to-add-a-custom-build-tool"></a>若要添加自定义生成工具  
  
1.  将项组添加到项目文件并添加每个输入文件的一个项。 指定命令、 其他输入、 输出和消息作为项元数据，如下所示。 此示例假定在你的项目所在的目录中存在的"faq.txt"文件。  
  
    ```  
    <ItemGroup>  
      <CustomBuild Include="faq.txt">  
        <Message>Copying readme...</Message>  
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>  
        <Outputs>$(OutDir)%(Identity)</Outputs>  
      </CustomBuild>  
    </ItemGroup>  
    ```  
  
### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>若要定义在其中在生成的自定义生成工具将执行  
  
1.  将以下属性组添加到项目文件。 你必须指定至少一个目标，但如果你只是想让你执行之前 （或之后） 的生成步骤，可以忽略另一个特定的目标。 在编译之后但在链接之前，此示例将执行的自定义步骤。  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## <a name="see-also"></a>请参阅  
 [演练： 使用 MSBuild 创建 Visual c + + 项目](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [如何： 在 MSBuild 项目中使用生成事件](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [如何：向 MSBuild 项目添加自定义生成步骤](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)
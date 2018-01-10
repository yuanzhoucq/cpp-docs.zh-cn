---
title: "如何： 向 MSBuild 项目添加自定义生成步骤 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msbuild.cpp.howto.addcustombuildstep
dev_langs: C++
helpviewer_keywords: 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d664b9fad6a9ec67dc009a90171119036dc13cde
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>如何：向 MSBuild 项目添加自定义生成步骤
自定义生成步骤是在生成中的用户定义步骤。 自定义生成步骤表现得像任何其他*命令工具*步骤中，如标准的编译或链接工具步骤。  
  
 在项目文件 (.vcxproj) 中指定的自定义生成步骤。 步骤可以指定命令行来执行，任何附加输入或输出文件，以及要显示的消息。 如果**MSBuild**确定输出文件已于输入文件而言已过期，则它将显示的消息并执行该命令。  
  
 若要指定自定义生成的位置的生成目标序列中的步骤，使用一个或两个`CustomBuildAfterTargets`和`CustomBuildBeforeTargets`项目文件中的 XML 元素。 例如，您无法指定自定义生成步骤运行之后链接工具目标和之前的清单工具目标。 实际的可用目标集取决于您的特定生成。  
  
 指定`CustomBuildBeforeTargets`元素之前的特定目标运行时，执行自定义生成步骤`CustomBuildAfterTargets`要执行该步骤后的特定目标运行时，元素或这两个元素执行两个相邻目标之间的步骤。 如果指定两个元素中，则将在其默认位置，这就是之后执行自定义生成工具**链接**目标。  
  
 自定义生成步骤和自定义生成工具共享中指定的信息`CustomBuildBeforeTargets`和`CustomBuildAfterTargets`XML 元素。 因此，这些目标只是一次在文件中指定项目。  
  
### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>若要定义由自定义生成步骤执行的内容  
  
1.  将属性组添加到项目文件。 在此属性组中，指定该命令、 输入和输出和消息，如下面的示例中所示。 此示例创建一个.cab 文件中创建的 main.cpp 文件从[演练： 使用 MSBuild 创建 Visual c + + 项目](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)。  
  
    ```  
    <ItemDefinitionGroup>  
      <CustomBuildStep>  
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>  
        <Outputs>$(TargetName).cab</Outputs>  
        <Inputs>$(TargetFileName)</Inputs>  
      </CustomBuildStep>  
    </ItemDefinitionGroup>  
    ```  
  
### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>若要定义自定义生成步骤，在生成中将执行  
  
1.  将以下属性组添加到项目文件。 你可以指定这两个目标，或如果你只是想要执行之前或之后的特定目标的自定义步骤可以忽略一个。 此示例告知**MSBuild**编译步骤完成之后但在链接步骤之前执行的自定义步骤。  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## <a name="see-also"></a>请参阅  
 [演练： 使用 MSBuild 创建 Visual c + + 项目](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [如何： 在 MSBuild 项目中使用生成事件](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [如何：向 MSBuild 项目添加自定义生成工具](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)
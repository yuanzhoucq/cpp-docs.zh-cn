---
title: "如何： 在 MSBuild 项目中使用生成事件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msbuild.cpp.howto.usebuildevents
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc8b3b21cdc9aad183f39bf709f93e022e790eef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>如何：在 MSBuild 项目中使用生成事件
生成事件是一个命令，[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]在生成过程中的特定阶段执行。 *预生成*事件发生在生成开始前;*预链接*事件发生在链接步骤开始; 之前和*后期生成*事件发生在生成后已成功结束。 仅当关联的生成步骤发生时，生成事件才会发生。 例如，如果链接步骤未运行，也不会发生 pre-link 事件。  
  
 每三个生成事件命令元素表示项定义组中 (`<Command>`) 执行和消息元素 (`<Message>`)，它是显示时**MSBuild**执行生成事件。 每个元素是可选的并且如果多次指定相同的元素，最后一个匹配项优先。  
  
 一个可选*在生成中使用*元素 (`<`*生成事件***UseInBuild**`>`) 可以在属性组，以指示中指定是否执行生成事件。 内容的价值*在生成中使用*元素可以是`true`或`false`。 默认情况下，除非执行生成事件其对应*在生成中使用*元素设置为`false`。  
  
 下表列出每个生成事件 XML 元素：  
  
|XML 元素|描述|  
|-----------------|-----------------|  
|`PreBuildEvent`|生成开始之前，将执行此事件。|  
|`PreLinkEvent`|此事件链接步骤开始之前执行。|  
|`PostBuildEvent`|在生成完成之后，将执行此事件。|  
  
 下表列出了每一个*在生成中使用*元素：  
  
|XML 元素|描述|  
|-----------------|-----------------|  
|`PreBuildEventUseInBuild`|指定是否执行*预生成*事件。|  
|`PreLinkEventUseInBuild`|指定是否执行*预链接*事件。|  
|`PostBuildEventUseInBuild`|指定是否执行*后期生成*事件。|  
  
## <a name="example"></a>示例  
 可以在中创建的 myproject.vcxproj 文件的项目元素内部添加下面的示例[演练： 使用 MSBuild 创建 Visual c + + 项目](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)。 A*预生成*事件使 main.cpp 的副本;*预链接*事件使 main.obj; 的副本和*后期生成*事件都提供了一份 myproject.exe。 如果使用发布配置生成项目时，才执行生成事件。 如果使用的调试配置生成项目时，不会执行生成事件。  
  
```  
<ItemDefinitionGroup>  
  <PreBuildEvent>  
    <Command>copy $(ProjectDir)main.cpp $(ProjectDir)copyOfMain.cpp</Command>  
    <Message>Making a copy of main.cpp </Message>  
  </PreBuildEvent>  
  <PreLinkEvent>  
 <Command>copy $(ProjectDir)$(Configuration)\main.obj $(ProjectDir)$(Configuration)\copyOfMain.obj</Command>  
    <Message>Making a copy of main.obj</Message>  
  </PreLinkEvent>  
  <PostBuildEvent>  
 <Command>copy $(ProjectDir)$(Configuration)\$(TargetFileName) $(ProjectDir)$(Configuration)\copyOfMyproject.exe</Command>  
    <Message>Making a copy of myproject.exe</Message>  
  </PostBuildEvent>  
</ItemDefinitionGroup>  
  
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">  
  <PreBuildEventUseInBuild>true</PreBuildEventUseInBuild>  
  <PreLinkEventUseInBuild>true</PreLinkEventUseInBuild>  
  <PostBuildEventUseInBuild>true</PostBuildEventUseInBuild>  
</PropertyGroup>  
  
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">  
  <PreBuildEventUseInBuild>false</PreBuildEventUseInBuild>  
  <PreLinkEventUseInBuild>false</PreLinkEventUseInBuild>  
  <PostBuildEventUseInBuild>false</PostBuildEventUseInBuild>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>请参阅  
 [MSBuild （Visual c + +）](../build/msbuild-visual-cpp.md)   
 [演练：使用 MSBuild 创建 Visual C++ 项目](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)
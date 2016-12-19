---
title: "如何：在 MSBuild 项目中使用生成事件 | Microsoft Docs"
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
  - "msbuild.cpp.howto.usebuildevents"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (c++), 如何：在项目中使用生成事件"
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：在 MSBuild 项目中使用生成事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

生成事件是 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 在生成过程中的特定阶段执行的命令。  *预先生成* 事件发生在生成开始前；*预链接* 事件发生在链接步骤开始前； *后期生成* 事件发生在生成成功结束之后。  只有当关联的生成步骤发生，生成事件发生。  例如，如果链接步骤未运行，则不会发生预链接事件。  
  
 在项目定义组中，这三个生成事件中的每一个生成事件都由所执行的命令元素 \(`<Command>`\) 和 **MSBuild** 该执行生成事件时所显示的消息元素 \(`<Message>`\) 来表示。  每个元素都是可选的，如果您多次指定同一元素，则最后一次优先。  
  
 可以在属性组中指定可选的“在生成中使用”元素（`<`*build\-event***UseInBuild**`>`），以指明是否执行生成事件。  “在生成中使用”元素的内容值为 `true` 或 `false`。  默认情况下，除非生成事件的对应“在生成中使用”元素设置为 `false`，否则将执行该生成事件。  
  
 下表列出了每个生成事件 XML 元素：  
  
|XML 元素|说明|  
|------------|--------|  
|`PreBuildEvent`|此事件在生成开始之前执行。|  
|`PreLinkEvent`|此事件在链接步骤开始之前执行。|  
|`PostBuildEvent`|此事件在生成完成后执行。|  
  
 下表列出了每个“在生成中使用”元素：  
  
|XML 元素|说明|  
|------------|--------|  
|`PreBuildEventUseInBuild`|指定是否执行预先生成事件。|  
|`PreLinkEventUseInBuild`|指定是否执行预链接事件。|  
|`PostBuildEventUseInBuild`|指定是否执行后期生成事件。|  
  
## 示例  
 以下示例可添加到在[演练：使用 MSBuild 创建 Visual C\+\+ 项目](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)中创建的 myproject.vcxproj 文件的 Project 元素内。  预先生成事件生成 main.cpp 的副本；预链接事件生成 main.obj 的副本；后期生成事件生成 myproject.exe 的副本。  如果项目是使用发布配置生成的，则执行生成事件。  如果项目是使用调试配置生成的，则不执行生成事件。  
  
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
  
## 请参阅  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)   
 [演练：使用 MSBuild 创建 Visual C\+\+ 项目](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)
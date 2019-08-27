---
title: 如何：在 MSBuild 项目中使用生成事件
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
ms.openlocfilehash: 3fe205223b6cf381bbf3e2872b1a84f9d81a3cb7
ms.sourcegitcommit: 2da5c42928739ca8cd683a9002598f28d8ec5f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2019
ms.locfileid: "70060065"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>如何：在 MSBuild 项目中使用生成事件

生成事件是 MSBuild 在生成过程中的特定阶段执行的命令。 生成前事件发生在生成开始之前;*预链接*事件发生在链接步骤开始之前:生成成功结束后, 会发生*生成后*事件。 仅当关联的生成步骤发生时，生成事件才会发生。 例如, 如果链接步骤未运行, 则不会发生预链接事件。

在项目定义组中, 每个生成事件都由执行的命令元素 (`<Command>`) 和在**MSBuild**执行生成事件时显示的消息元素 (`<Message>`) 表示。 每个元素都是可选的, 如果多次指定同一个元素, 则最后一个匹配项优先。

可以在属性组中指定一个可选的`<`*内部生成*元素 (*生成事件*`UseInBuild>`), 以指示是否执行生成事件。 *使用内部*元素的内容的值为**true**或**false**。 默认情况下, 将执行生成事件, 除非其相应的 *"使用内部版本"* 元素设置`false`为。

下表列出了每个生成事件 XML 元素:

|XML 元素|描述|
|-----------------|-----------------|
|`PreBuildEvent`|此事件在生成开始之前执行。|
|`PreLinkEvent`|此事件在链接步骤开始之前执行。|
|`PostBuildEvent`|此事件在生成完成后执行。|

下表列出了每个*使用中*的元素:

|XML 元素|描述|
|-----------------|-----------------|
|`PreBuildEventUseInBuild`|指定是否执行*预先生成*事件。|
|`PreLinkEventUseInBuild`|指定是否执行*预链接*事件。|
|`PostBuildEventUseInBuild`|指定是否执行*生成后*事件。|

## <a name="example"></a>示例

下面的示例可以添加到在演练中[创建的 myproject 文件的项目元素内:使用 MSBuild 创建](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md) C++项目。 *预先生成*事件会生成 main .cpp 的副本;*预链接*事件创建 main .obj 副本;*生成后*事件会生成 myproject 的副本。 如果项目是使用发布配置生成的, 则将执行生成事件。 如果项目是使用调试配置生成的, 则不会执行生成事件。

``` xml
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

[命令行上的 MSBuild - C++](msbuild-visual-cpp.md)<br/>
[演练：使用 MSBuild 创建 C++ 项目](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)

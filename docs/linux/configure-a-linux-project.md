---
title: "配置 Linux 项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 1683c03c522b0b332ced9e93188c65e996ac633d
ms.openlocfilehash: ec7ec2a7f5f0393f00efb6d662494e7be2a3f696
ms.lasthandoff: 03/22/2017

---

# <a name="configure-a-linux-project"></a>配置 Linux 项目

## <a name="general-settings"></a>常规设置
可以使用 Visual Studio 为 Linux 项目配置各种选项。  若要查看这些选项，请选择“**项目 > 属性**”菜单，或在“**解决方案资源管理器**”中右键单击相应项目，然后从上下文菜单中选择“**属性**”：

![常规配置](media/settings_general.png)

默认情况下，可执行文件 (.out) 是使用该工具生成的。  若要生成静态或动态库，或使用现有生成文件，请使用“**配置类型**”选项。

## <a name="remote-settings"></a>远程设置
若要更改与远程 Linux 计算机相关的设置，请选择“**远程设置**”项：

![远程设置](media/settings_remote.png)

* 若要更改目标 Linux 计算机，请使用“**目标计算机**”条目。  这可以让你选择之前创建的连接之一。  若要创建新条目，请参阅[连接到远程 Linux 计算机](connect-to-your-remote-linux-computer.md)部分。

* “**远程根目录**”确定在远程 Linux 计算机上生成项目的根位置。  除非更改，否则该位置默认为 **~/projects**。

* “**远程项目目录**”是在远程 Linux 计算机上生成此特定项目的位置。  该位置默认为 **$(RemoteRootDir)/$(ProjectName)**，它将扩展到以当前项目命名的目录，在上面设置的根目录下。

* 最后，若要更改默认的 C 和 C++ 编译器，或者用于生成项目的链接器和存档程序，请使用“**工具默认**”部分中的相应条目。  可以将这些条目设置为使用 GCC 的某个版本，例如甚至是使用 Clang 编译器。

## <a name="vc-directories"></a>VC++ 目录
默认情况下，Visual Studio 不包括来自 Linux 计算机的任何系统级包含文件。  例如，Visual Studio 中不存在 **/usr/include** 目录中的项。  如需完整的 [IntelliSense](/visualstudio/ide/using-intellisense) 支持，你需要将这些文件复制到开发计算机上的某个位置，并将 Visual Studio 指向此位置。  一种选择是使用 scp（安全复制）来复制这些文件。  在 Windows 10 上，你可以使用 [Windows 上的 Bash](https://msdn.microsoft.com/commandline/wsl/about) 来运行 scp。  对于之前版本的 Windows，你可以使用类似 [PSCP（PuTTY 安全复制）](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)来操作。

可以使用类似如下命令复制文件：

`scp -r linux_username@remote_host:/usr/include .`

当然，也可以使用使用适合自己环境的值替换 **linux_username** 和 **remote_host** 值。

复制文件后，使用项目属性中的“**VC++ 目录**”项告诉 Visual Studio 在哪里可以找到刚复制的其他包含文件。

![VC++ 目录](media/settings_directories.png)

## <a name="copy-sources"></a>复制源文件
进行生成时，将开发 PC 上的源文件复制到 Linux 计算机并在那里进行编译。  默认情况下，Visual Studio 项目中的所有源文件都将复制到上述设置中设置的位置。  但是，也可以将其他源文件添加到此列表，或完全关闭复制源文件，这是生成文件项目的默认值。

* “**要复制的源**”确定将哪些源文件复制到远程计算机。  在默认情况下，**@(SourcesToCopyRemotely)** 默认为项目中的所有源代码文件，但不包含任何资产/资源文件，如映像。

* 可以打开和关闭“**复制源**”，以启用和禁用将源文件复制到远程计算机操作。

* “**要复制的其他源**”允许添加将复制到远程系统的其他源文件。  可以指定以分号分隔的列表，也可以使用 **:=** 语法指定要使用的本地和远程名称：

  `C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>生成事件
由于所有编译都是在远程计算机上进行的，因此，已将数个其他生成事件添加到“项目属性”中的“生成事件”部分。  这些是“**远程预生成事件**”、“**远程预链接事件**”和“**删除生成后事件**”，并且将在此过程中的各个步骤之前或之后在远程计算机上发生。

![生成事件](media/settings_buildevents.png)

## <a name="see-also"></a>另请参阅
[使用项目属性](../ide/working-with-project-properties.md)

---
title: vcpkg - 用于 Windows、Linux 和 MacOS 的 C++ 包管理器 | Microsoft Docs
description: vcpkg 是一种命令行程序包管理器，可极大简化 Windows 上的开源 C++ 库的购置与安装。
keywords: vcpkg
author: mikeblome
ms.author: mblome
ms.date: 05/14/2018
ms.technology:
- cpp-ide
ms.tgt_pltfrm: windows
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.topic: conceptual
dev_langs:
- C++
ms.workload:
- cplusplus
ms.openlocfilehash: af51ee7c6fa4e1243b400be58ac22ba833cfae80
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705434"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg：用于 Windows、Linux 和 MacOS 的 C++ 包管理器

vcpkg 是一种命令行包管理器，可极大简化 Windows、Linux 和 MacOS 上第三方库的购置与安装。 如果项目要使用第三方库，建议通过 vcpkg 来安装它们。 vcpkg 同时支持开源和专有库。 已测试 vcpkg Windows 目录中所有库与 Visual Studio 2015 及 Visual Studio 2017 的兼容性。 截至 2018 年 5 月，Windows 目录中已有 900 多个库，Linux/MacOS 目录中有 350 多个库。 C++ 社区正在不断向两个目录添加更多的库。

## <a name="simple-yet-flexible"></a>简单而灵活

仅通过单个命令就能下载源并生成库。 vcpkg 本身就是一个开源项目，可通过 GitHub 获取。 可凭喜好自定义个人专用克隆。 例如，除在公共目录中找到的内容外，还可指定不同的库或不同版本的库。 可在单台计算机上拥有多个 vcpkg 克隆，每个克隆都可生成自定义库集和/或编译开关等。每个克隆都是一个自包含、x 可复制的环境，它自身的 vcpkg.exe 副本仅可在自己的层次结构中运行。 vcpkg 不会被添加到任何环境变量，并且在 Windows 注册表或 Visual Studio 上也不会有依赖项。

## <a name="sources-not-binaries"></a>源不是二进制文件

对于 Windows 目录中的库，vcpkg 会下载源，而不是二进制文件[1]。 它将使用 Visual Studio 2017 或 Visual Studio 2015（如果未安装 Visual Studio 2017）对源进行编译。 在 C++ 中，作为链接到它的应用程序代码，使用相同的编译器及编译器版本来编译任何要用的库至关重要。 通过 vcpkg 可以消除或最大程度减少不匹配二进制文件的存在风险及它可能造成的问题。 对于使用特定编译器版本的标准化团队，可让一位成员使用 vcpkg 下载源并编译一组二进制文件，然后通过导出命令将二进制文件和标头压缩打包，即可与其他团队成员进行共享。 有关详细信息，请参阅下方的[导出已编译二进制文件及标头](#export_binaries_per_project)。

如果在端口集合中使用专用库创建 vcpkg 克隆，则可以添加一个端口来下载预生成二进制文件和标头，并编写一个 portfile.cmake 文件，轻松将上述文件复制到所需的地方。

[1] 注意：某些专有库不具有这些源。在这些情况下，vcpkg 将下载可兼容预生成二进制文件。*

## <a name="installation"></a>安装 

从 GitHub 克隆 vcpkg 存储库：https://github.com/Microsoft/vcpkg. 可凭喜好下载到任意文件夹位置。

在根文件夹中运行 bootstrapper： 

- **bootstrap-vcpkg.bat** (Windows)
- **./bootstrap-vcpkg.sh** (Linux、MacOS)

## <a name="search-the-list-of-available-libraries"></a>在列表中搜索可用库

要查看哪些包可用，请在命令提示符中键入：vcpkg search

此命令枚举 vcpkg/ports 子文件夹中的控件文件。 将出现如下的文件列表：

```cmd
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. \<https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

可以根据模式筛选，例如 vcpkg search ta：

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library

```

### <a name="install-a-library-on-your-local-machine"></a>在本地计算机上安装库

在使用 vcpkg search 获取库的名称后，可使用 vcpkg install 下载库并对其进行编译。 vcpkg 在端口目录中使用库的端口文件。 如果未指定三元组，则 vcpkg 将针对目标平台的默认三元组进行安装和编译：x86-windows、x64-linux.cmake 或 x64-osx.cmake。

对于 Linux 库，vcpkg 取决于本地计算机上安装的 gcc。 在 MacOS 上，vcpkg 使用 Clang。 

如果端口文件指定了依赖项，vcpkg 还会下载并安装这些依赖项。 下载完成后，vcpkg 使用库所使用的生成系统（版本不限）来生成库。 首选 CMake 和 MSBuild（Windows 上）项目，但同时还支持 MAKE 以及其他任何生成系统。 如果 vcpkg 在本地计算机上找不到指定的生成系统，它会下载并安装一个。

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.

```

对于 CMAKE 项目，使用 CMAKE_TOOLCHAIN_FILE 实现库与 `find_package()` 的结合使用。 例如:  

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake (Linux/MacOS)
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake (Windows)
```

## <a name="list-the-libraries-already-installed"></a>列出已安装的库

在安装某些库以后，可使用 vcpkg list 来查看所获得的内容：

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

## <a name="integrate-with-visual-studio-windows"></a>与 Visual Studio (Windows) 集成

### <a name="per-user"></a>按用户

运行 vcpkg integrate install 来配置 Visual Studio，以便按用户找到所有 vcpkg 头文件和二进制文件，同时还无需手动编辑 VC++ 目录路径。 如果有多个克隆，则运行此命令的克隆将成为新的默认位置。

现在，只需键入文件夹/标头就可轻松加入标头，自动完成功能将帮助你完成这一切。 在链接到 lib 或添加项目引用时，无需额外步骤。 下图演示了 Visual Studio 查找 azure-storage-cpp 标头的方法。 vcpkg 将其标头放置在 /installed 子文件夹中，由目标平台予以分区。 下图显示库的 /was 子文件夹中包含文件的列表：

![vcpkg IntelliSense 集成](media/vcpkg-intellisense.png "vcpkg 和 IntelliSense")

### <a name="per-project"></a>按项目

如果需要使用的库的版本与活动 vcpkg 实例中的版本不同，请按以下步骤操作：

1. 新建 vcpkg 克隆
1. 修改库的端口文件以获取所需版本
1. 运行 vcpkg install \<library>。
1. 使用 vcpkg integrate project 创建 NuGet 包，它会按项目来引用该库。

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>与 Visual Studio Code (Linux/MacOS) 集成 

运行 vcpkg integrate install，使用 vcpkg 登记的位置在 Linux/MacOS 上配置 Visual Studio Code，并在源文件上启用 IntelliSense。

## <a name="target-linux-from-windows-via-wsl"></a>通过 WSL 从 Windows 指向 Linux

可使用适用于 Linux 的 Windows 子系统 (WSL) 从 Windows 计算机生成 Linux 二进制文件。 按照说明[在 Windows 10 上设置 WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10)，并使用[适用于 Linux 的 Visual Studio 扩展](https://blogs.msdn.microsoft.com/vcblog/2017/02/08/targeting-windows-subsystem-for-linux-from-visual-studio/)进行配置。 可将生成的所有 Windows 和 Linux 库放在同一文件夹中，并从 Windows 和 WSL 进行访问。


## <a name="export_binaries_per_project"></a>导出已编译的二进制文件和标头

让团队中的每个成员都去下载和生成库可能会造成效率低下。 一个团队成员就可完成该工作，然后使用 vcpkg export 创建二进制文件和标头的 zip 文件或 NuGet 包（各种格式均可），将其与其他团队成员进行轻松共享。

## <a name="updateupgrade-installed-libraries"></a>更新/升级已安装的库

公共目录始终与最新版本的库保持一致。 要判断哪个本地库已过期，请使用 vcpkg update。 准备好将端口集合更新为公共目录的最新版本后，运行 vcpkg upgrade 命令以自动下载和重新生成任一或所有已安装的过期库。

默认情况下，upgrade 命令仅列出过期库；而不会对它们进行升级。 要执行升级操作，请使用 --no-dry-run 选项。

```cmd
  vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>升级选项

- **--no-dry-run** 执行升级，在没有指定条件的情况下，命令只列出过期的包。
- **--keep-going** 继续安装包（即使出现了失败）。
- **--triplet \<t>** 为非限定的包设置默认的三元组。
- **--vcpkg-root \<path>** 指定要使用的 vcpkg 目录，而不是使用当前目录或工具目录。

### <a name="upgrade-example"></a>升级示例

以下示例演示如何只升级指定的库。 请注意，必要时 vcpgk 会自动拉取依赖项。

```cmd
c:\users\satyan\vcpkg> vcpkg upgrade tiny-dnn:x86-windows zlib
The following packages are up-to-date:
   tiny-dnn:x86-windows

The following packages will be rebuilt:
    * libpng[core]:x86-windows
    * tiff[core]:x86-windows
      zlib[core]:x86-windows
Additional packages (*) will be modified to complete this operation.
If you are sure you want to rebuild the above packages, run this command with the --no-dry-run option.
```

## <a name="contribute-new-libraries"></a>发布新库

可以在自己的专用端口集合中添加任意库。 要建议适合公共目录的新库，请在 [GitHub vcpkg 问题页](https://github.com/Microsoft/vcpkg/issues)上打开一个问题。

## <a name="remove-a-library"></a>删除库

键入 vcpkg remove 可删除已安装的库。 如果存在任何其他依赖于它的库，则系统会提示通过 --recurse 重新运行命令，如执行此操作，则下游的所有库都会被删除。

## <a name="customize-vcpkg"></a>自定义 vcpkg

可凭自身喜好随意修改 vcpkg 的克隆。 可创建多个 vcpkg 克隆，修改每个克隆中的端口文件，使其包含特定版本的库或指定命令行参数。 例如在某企业中，某组的开发者可能正在使用拥有某一依赖项集的软件，而其他组可能拥有不同的集。 可设置两个 vcpkg 克隆并对其进行修改，以便根据需要来下载不同版本的库和编译开关等。

## <a name="uninstall-vcpkg"></a>卸载 vcpkg

只需删除目录。

## <a name="send-feedback-about-vcpkg"></a>发送关于 vcpkg 反馈

使用 vcpkg contact --survey 命令向 Microsoft 发送关于 vcpkg 的反馈，包括 Bug 报告和功能上的建议。

## <a name="the-vcpkg-folder-hierarchy"></a>vcpkg 文件夹层次结构

所有 vcpkg 功能和数据都自包含在称为“实例”的单独目录层次结构中。 没有注册表设置或环境变量。 可以在计算机上设置任意数量的 vcpkg 实例，它们彼此互不干扰。

vcpkg 实例的内容如下：

- buildtrees - 包含从中生成每个库的源的子文件夹
- docs - 文档和示例
- downloads - 任何已下载工具或源的缓存副本。 运行安装命令时，vcpkg 会首先搜索此处。
- installed - 包含每个已安装库的标头和二进制文件。 与 Visual Studio 集成时，实质上相当于告知它将此文件夹添加到其搜索路径。
- packages - 在不同的安装之间用于暂存的内部文件夹。
- ports - 用于描述每个库的目录、版本和下载位置的文件。 如有需要，可添加自己的端口。
- scripts - 由 vcpkg 使用的脚本（cmake、powershell）。
- toolsrc - vcpkg 和相关组件的 C++ 源代码
- triplets - 包含每个受支持目标平台（如 x86-windows 或 x64-uwp）的设置。

## <a name="command-line-reference"></a>命令行参考

|命令|描述|
|---------|---------|
|**vcpkg search [pat]**|搜索可安装的包|
|**vcpkg install \<pkg>...**|安装包|
|**vcpkg remove \<pkg>...**|卸载包|
|**vcpkg remove --outdated**|卸载所有过期包|
|**vcpkg list**|列出已安装的包|
|**vcpkg update**|显示用于更新的包列表|
|**vcpkg upgrade**|重新生成所有过期包|
|**vcpkg hash \<file> [alg]**|通过特定算法对文件执行哈希操作，默认为 SHA512|
|**vcpkg integrate install**|使已安装包在用户范围内可用。 首次使用时需要管理权限|
|**vcpkg integrate remove**|删除用户范围的集成|
|**vcpkg integrate project**|为使用单个 VS 项目生成引用 NuGet 包|
|**vcpkg export \<pkg>... [opt]...**|导出包|
|**vcpkg edit \<pkg>**|打开端口进行编辑（使用 %EDITOR%，默认为“code”）|
|**vcpkg create \<pkg> \<url> [archivename]**|创建新程序包|
|**vcpkg cache**|列出缓存的已编译包|
|**vcpkg version**|显示版本信息|
|**vcpkg contact --survey**|显示联系信息，以便发送反馈。|

### <a name="options"></a>选项

|选项|描述|
|---------|---------|
|**--triplet \<t>**|指定目标体系结构三元组。 （默认：`%VCPKG_DEFAULT_TRIPLET%`，另请参阅“vcpkg help triplet”）|
|**--vcpkg-root \<path>**|指定 vcpkg 根目录（默认：`%VCPKG_ROOT%`）|


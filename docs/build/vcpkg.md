---
title: vcpkg：用于 Windows、Linux 和 MacOS 的 C++ 包管理器
description: vcpkg 是一种命令行包管理器，可极大简化 Windows、MacOS 和 Linux 上开源 C++ 库的购置与安装。
ms.date: 01/10/2020
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: 7c3dddd62a66c746d92d2f931b97e354ee27d75f
ms.sourcegitcommit: ba129dc55dc3ff638f3af5ac0e87ec2ca1cb2674
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75869713"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg：用于 Windows、Linux 和 MacOS 的 C++ 包管理器

vcpkg 是用于 C++ 的一种命令行包管理器。 它极大地简化了 Windows、Linux 和 MacOS 上第三方库的购置与安装。 如果项目要使用第三方库，建议通过 vcpkg 来安装它们。 vcpkg 同时支持开源和专有库。 已测试 vcpkg Windows 目录中所有库与 Visual Studio 2015、Visual Studio 2017 及 Visual Studio 2019 的兼容性。 在 Windows 和 Linux/MacOS 目录之间，vcpkg 现已支持超过 1900 个库。 C++ 社区正在不断向两个目录添加更多的库。

## <a name="simple-yet-flexible"></a>简单而灵活

仅通过单个命令就能下载源并生成库。 vcpkg 本身就是一个开源项目，可通过 GitHub 获取。 你可以按照自己喜欢的任何方式自定义你的专用 vcpkg 克隆。 例如，除了在公共目录中找到的内容外，还可以指定不同的库或不同版本的库。 一台计算机上可以有多个 vcpkg 克隆。 每一克隆都可以设置为生成带有你首选的编译开关的自定义库集合。 每个克隆都是一个自包含的环境，它自身的 vcpkg.exe 副本仅可在自己的层次结构中运行。 vcpkg 不会被添加到任何环境变量中，并且在 Windows 注册表或 Visual Studio 上也没有依赖项。

## <a name="sources-not-binaries"></a>是源，而不是二进制文件

对于 Windows 目录中的库，vcpkg 会下载源，而不是二进制文件<sup>1</sup>。 它使用可以找到的最新版 Visual Studio 编译这些源代码。 在 C++ 中，有一点至关重要，即你的应用程序代码以及你所使用的任何库应均是由同一编译器和编译器版本编译的。 通过 vcpkg 可以消除或最大程度减少不匹配二进制文件的存在风险及它可能造成的问题。 对于使用特定编译器版本的标准化团队而言，可让一位成员使用 vcpkg 下载源并编译一组二进制文件。 他们随后可以使用导出命令将二进制文件和标头进行压缩打包，从而与其他团队成员共享。 有关详细信息，请参阅下方的[导出已编译二进制文件及标头](#export_binaries_per_project)。

你还可以创建一个包含端口集合中的专用库的 vcpkg 克隆。 添加一个可下载预生成的二进制文件和标头的端口。 然后，编写一个仅将这些文件复制到首选位置的 portfile.cmake 文件。

<sup>1</sup> 注意：这些源不适用于某些专有库。  在这些情况下，vcpkg 会下载兼容的预生成二进制文件。

## <a name="installation"></a>安装

从 GitHub 克隆 vcpkg 存储库：[https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg)。 可凭喜好下载到任意文件夹位置。

在根文件夹中运行 bootstrapper：

- **bootstrap-vcpkg.bat** (Windows)
- **./bootstrap-vcpkg.sh** (Linux、MacOS)

## <a name="search-the-list-of-available-libraries"></a>搜索可用库列表

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

在使用 vcpkg search 获取库的名称后，可使用 vcpkg install 下载库并对其进行编译   。 vcpkg 在端口目录中使用库的端口文件。 如果未指定三元组，则 vcpkg 将针对目标平台的默认三元组进行安装和编译：x86-windows、x64-linux.cmake 或 x64-osx.cmake。

对于 Linux 库，vcpkg 取决于本地计算机上安装的 GCC。 在 MacOS 上，vcpkg 使用 Clang。

当端口文件指定了依赖项时，vcpkg 也会下载并安装这些依赖项。 下载后，vcpkg 将使用库所使用的同一生成系统生成库。 CMake 和 MSBuild（Windows 上）项目是首选，但同时还支持 MAKE 以及其他任何生成系统。 如果 vcpkg 在本地计算机上找不到指定的生成系统，它会下载并安装一个。

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

对于 CMAKE 项目，通过 CMAKE_TOOLCHAIN_FILE 来配合使用库和 `find_package()`。 例如：

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake (Linux/MacOS)
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake (Windows)
```

## <a name="list-the-libraries-already-installed"></a>列出已安装的库

在安装了某些库后，你可以使用 vcpkg list 来查看所获得的内容  ：

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

运行 vcpkg integrate install 来配置 Visual Studio，以便按用户找到所有 vcpkg 标头文件和二进制文件  。 无需手动编辑 VC++ 目录路径。 如果有多个克隆，那么你从中运行此命令的克隆则将成为新的默认位置。

现在，只需键入文件夹/标头即可轻松加入 (#include) 标头，并且自动完成功能将帮助你完成这一切。 在链接到 lib 或添加项目引用时，无需额外步骤。 下图演示了 Visual Studio 查找 azure-storage-cpp 标头的方法。 vcpkg 将其标头放置在 /installed 子文件夹中，由目标平台予以分区  。 下图显示库的 /was 子文件夹中包含文件的列表  ：

![vcpkg 和 IntelliSense](media/vcpkg-intellisense.png "vcpkg 和 IntelliSense")

### <a name="per-project"></a>按项目

如果需要使用的库的版本与活动 vcpkg 实例中的版本不同，请按以下步骤操作：

1. 新建 vcpkg 克隆
1. 修改库的端口文件以获取所需版本
1. 运行 vcpkg install \<library>  。
1.  使用 vcpkg integrate project 创建 NuGet 包，它会按项目来引用该库。

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>与 Visual Studio Code (Linux/MacOS) 集成

运行 vcpkg integrate install 在 Linux/MacOS 上配置 Visual Studio Code  。 此命令将设置 vcpkg 登记的位置，并对源文件启用 IntelliSense。

## <a name="target-linux-from-windows-via-wsl"></a>通过 WSL 从 Windows 指向 Linux

可使用适用于 Linux 的 Windows 子系统（也称为 WSL）在 Windows 计算机上生成 Linux 二进制文件。 按照说明[在 Windows 10 上设置 WSL](/windows/wsl/install-win10)，并使用[适用于 Linux 的 Visual Studio 扩展](https://blogs.msdn.microsoft.com/vcblog/2017/02/08/targeting-windows-subsystem-for-linux-from-visual-studio/)进行配置。 可以将所有针对 Windows 和 Linux 生成的库放入同一文件夹中。 可以从 Windows 和 WSL 访问它们。

## <a name="export_binaries_per_project"></a>导出已编译的二进制文件和标头

让团队中的每位成员都下载和生成公用库是一种效率较低的做法。 可以单独让一位团队成员使用 vcpkg export 命令创建二进制文件和标头的通用 zip 文件，或者创建 NuGet 包  。 然后，可以轻松地将它与其他团队成员共享。

## <a name="updateupgrade-installed-libraries"></a>更新/升级已安装的库

公共目录始终与最新版本的库保持一致。 要判断哪个本地库已过期，请使用 vcpkg update  。 准备好将端口集合更新到最新版本的公共目录后，请运行 vcpkg upgrade 命令  。 它会自动下载并重新生成已过期的任意或所有已安装的库。

 默认情况下，upgrade 命令仅列出过期库；而不会对它们进行升级。 若要真正升级这些库，请使用 --no-dry-run 选项  。

```cmd
  vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>升级选项

- **--no-dry-run** 执行升级，在没有指定条件的情况下，命令只列出过期的包。
- **--keep-going** 继续安装包（即使出现了失败）。
- **--triplet \<t>** 为非限定的包设置默认的三元组。
- **--vcpkg-root \<path>** 指定要使用的 vcpkg 目录，而不是使用当前目录或工具目录。

### <a name="upgrade-example"></a>升级示例

以下示例演示如何只升级指定的库。 必要时 vcpkg 会自动拉取依赖项。

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

键入 vcpkg remove  可删除已安装的库。 如果存在任何其他依赖于它的库，则系统会提示你使用 --recurse 重新运行命令，如执行此操作，则下游的所有库都会被删除  。

## <a name="customize-vcpkg"></a>自定义 vcpkg

可凭自身喜好随意修改 vcpkg 的克隆。 你甚至可以创建多个 vcpkg 克隆，然后在每个克隆中修改端口文件。 这是获取特定库版本或指定特定命令行参数的一种简单方法。 例如，在企业中，各个开发人员组可能在具有一组特定于他们所在组的依赖项的软件上工作。 解决方法是为每个团队设置一个 vcpkg 的克隆。 然后，修改克隆以下载库版本，并设置每个团队需要的编译开关。

## <a name="uninstall-vcpkg"></a>卸载 vcpkg

只需删除 vcpkg 目录。 删除此目录会卸载 vcpkg 分发以及 vcpkg 已安装的所有库。

## <a name="send-feedback-about-vcpkg"></a>发送关于 vcpkg 的反馈

使用 vcpkg contact --survey 命令向 Microsoft 发送关于 vcpkg 的反馈，包括 Bug 报告和功能上的建议  。

## <a name="the-vcpkg-folder-hierarchy"></a>vcpkg 文件夹层次结构

所有 vcpkg 功能和数据都自包含在称为“实例”的单独目录层次结构中。 没有注册表设置或环境变量。 可以在一台计算机上设置任意数量的 vcpkg 实例，它们彼此互不干扰。

vcpkg 实例的内容如下：

- buildtrees - 包含从中生成每个库的源的子文件夹
- docs - 文档和示例
- downloads - 任何已下载工具或源的缓存副本。 运行安装命令时，vcpkg 会首先搜索此处。
- installed - 包含每个已安装库的标头和二进制文件。 与 Visual Studio 集成时，实质上是相当于告知它将此文件夹添加到其搜索路径。
- packages - 在不同的安装之间用于暂存的内部文件夹。
- ports - 用于描述每个库的目录、版本和下载位置的文件。 如有需要，可添加自己的端口。
- scripts - 由 vcpkg 使用的脚本（cmake、powershell）。
- toolsrc - vcpkg 和相关组件的 C++ 源代码
- triplets - 包含每个受支持目标平台（如 x86-windows 或 x64-uwp）的设置。

## <a name="command-line-reference"></a>命令行参考

|命令|描述|
|---------|---------|
|**vcpkg search \[pat]**|搜索可安装的包|
|**vcpkg install \<pkg>...**|安装包|
|**vcpkg remove \<pkg>...**|卸载包|
|**vcpkg remove --outdated**|卸载所有过期包|
|**vcpkg list**|列出已安装的包|
|**vcpkg update**|显示用于更新的包列表|
|**vcpkg upgrade**|重新生成所有过期包|
|**vcpkg hash \<file> \[alg]**|通过特定算法对文件执行哈希操作，默认为 SHA512|
|**vcpkg integrate install**|使已安装包在用户范围内可用。 首次使用时需要管理权限|
|**vcpkg integrate remove**|删除用户范围的集成|
|**vcpkg integrate project**|为使用单个 VS 项目生成引用 NuGet 包|
|**vcpkg export \<pkg>... \[opt]...**|导出包|
|**vcpkg edit \<pkg>**|打开端口进行编辑（使用 %EDITOR%，默认为“code”）|
|**vcpkg create \<pkg> \<url> \[archivename]**|创建新程序包|
|**vcpkg cache**|列出缓存的已编译包|
|**vcpkg version**|显示版本信息|
|**vcpkg contact --survey**|显示联系信息，以便发送反馈。|

### <a name="options"></a>选项

|选项|描述|
|---------|---------|
|**--triplet \<t>**|指定目标体系结构三元组。 （默认：`%VCPKG_DEFAULT_TRIPLET%`，另请参阅“vcpkg help triplet”  ）|
|**--vcpkg-root \<path>**|指定 vcpkg 根目录（默认：`%VCPKG_ROOT%`）|

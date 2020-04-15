---
title: 可视化工作室视觉工作室项目中的 Clang/LLVM 支持
ms.date: 08/30/2019
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: 8d7d7fec979d3e7b8f665e56094ee1c309e3b686
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323124"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>可视化工作室项目中的 Clang/LLVM 支持

::: moniker range="<=vs-2017"

在 Visual Studio 2019 中提供了对 CMake 和 MSBuild 项目的 Clang 支持。

::: moniker-end

::: moniker range="vs-2019"

您可以将 Visual Studio 2019 版本 16.2 与 Clang 一起用于编辑、构建和调试面向 Windows 或 Linux 的C++可视化工作室项目 （MSBuild）。

## <a name="install"></a>安装

为了在 Visual Studio 中获得最佳 IDE 支持，我们建议使用 Windows 的最新 Clang 编译器工具。 如果还没有这些，则可以通过打开 Visual Studio 安装程序并选择**C++ Clang 工具来安装这些这些工具，用于****桌面开发下的 Windows，C++** 可选组件。 如果您希望在计算机上使用现有的 Clang 安装，请选择**v142 生成工具的clang-clC++。** 可选组件。 微软C++标准库目前至少需要Clang 8.0.0;Clang 的捆绑版本将自动更新，以在标准库的 Microsoft 实现中保持最新更新。

![Clang 组件安装](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>将 Windows 项目配置为使用 Clang 工具

要将 Visual Studio 项目配置为使用 Clang，请右键单击**解决方案资源管理器**中的项目节点并选择 **"属性**"。 通常，应首先选择对话框顶部**的所有配置**。 然后，在**常规** > **平台工具集**下，选择**LLVM （clang-cl），** 然后**确定**。

![Clang 组件安装](media/clang-msbuild-prop-page.png)

如果您使用的是与 Visual Studio 捆绑的 Clang 工具，则无需执行其他步骤。 对于 Windows 项目，Visual Studio 默认情况下以[clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf)模式调用 Clang，并与标准库的 Microsoft 实现链接。 默认情况下 **，clang-cl.exe**位于`C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`中。

如果使用自定义 Clang 安装，则可以通过添加自定义 Clang 安装根作为第一个目录来修改**项目** > **属性** > **VC++ DIrectories** > **配置属性** > **可执行目录**，或者更改`LLVMInstallDir`属性的值。 有关详细信息[，请参阅设置自定义 LLVM 位置](#custom_llvm_location)。

## <a name="configure-a-linux-project-to-use-clang-tools"></a>将 Linux 项目配置为使用 Clang 工具

对于 Linux 项目，Visual Studio 使用 Clang GCC 兼容的前端。 项目属性和几乎所有编译器标志都相同

要将可视化工作室 Linux 项目配置为使用 Clang：

1. 右键单击**解决方案资源管理器**中的项目节点并选择**属性**。
1. 通常，应首先选择对话框顶部**的所有配置**。
1. 在 **"常规**>**平台工具集**"下，选择**WSL_Clang_1_0**是否正在使用适用于 Linux 的 Windows 子系统，或者选择**Remote_Clang_1_0**是否使用远程计算机或 VM。
1. 按 **“确定”**。

![Clang 组件安装](media/clang-msbuild-prop-page.png)

在 Linux 上，Visual Studio 默认情况下使用它在 PATH 环境属性中遇到的第一个 Clang 位置。 如果使用自定义 Clang 安装，则必须`LLVMInstallDir`更改属性的值，否则替换**项目** > **属性** > **VC++ DIrecres** > **配置属性** > **可执行目录**下的路径。 有关详细信息[，请参阅设置自定义 LLVM 位置](#custom_llvm_location)。

## <a name="set-a-custom-llvm-location"></a><a name="custom_llvm_location"></a>设置自定义 LLVM 位置

您可以通过创建*Directory.build.props*文件并将该文件添加到任何项目的根文件夹，为一个或多个项目设置 LLVM 的自定义路径。 您可以将其添加到根解决方案文件夹中，将其应用于解决方案中的所有项目。 该文件应如下所示（但替换实际路径）：

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>设置其他属性、编辑、生成和调试

设置 Clang 配置后，右键单击项目节点并选择 **"重新加载项目**"。 现在，您可以使用 Clang 工具生成和调试项目。 Visual Studio 检测到您正在使用 Clang 编译器，并提供 IntelliSense、突出显示、导航和其他编辑功能。 错误和警告显示在**输出窗口中**。 Clang 配置的项目属性页与 MSVC 的项目属性页非常相似，尽管某些与编译器相关的功能（如"编辑"和"继续"）不适用于 Clang 配置。 要设置属性页中不可用的 Clang 编译器或链接器选项，可以在**配置属性** > **C/C++（或链接器）** > **命令行** > **附加选项**下的属性页中手动添加该选项。

调试时，可以使用断点、内存和数据可视化以及大多数其他调试功能。  

![Clang 调试](media/clang-debug-msbuild.png)

::: moniker-end

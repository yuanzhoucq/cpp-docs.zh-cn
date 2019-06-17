---
title: 配置 Linux 项目以使用地址擦除器
description: 介绍如何在 Visual Studio 中配置 C++ Linux 项目以使用地址擦除器。
ms.date: 06/07/2019
ms.openlocfilehash: 2415e8971614de35f046b699ce99c3822faf9372
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2019
ms.locfileid: "66824171"
---
# <a name="configure-linux-projects-to-use-address-sanitizer"></a>配置 Linux 项目以使用地址擦除器

在 Visual Studio 2019 版本 16.1 中，AddressSanitizer (ASan) 支持已集成到 Linux 项目。 可以为基于 MSBuild 的 Linux 项目和 CMake 项目启用 ASan。 它可在远程 Linux 系统和适用于 Linux 的 Windows 子系统 (WSL) 上运行。

## <a name="about-asan"></a>关于 ASan

ASan 是 C/C++ 的运行时内存错误检测器，可捕获以下错误：

- 释放后使用（无关联的指针引用）
- 堆缓冲区溢出
- 堆栈缓冲区溢出
- 返回后使用
- 审视后使用
- 初始化顺序 bug

当 ASan 检测到错误时，它会立即停止执行。 如果在调试程序中运行启用了 ASan 的程序，系统会显示一条消息，其中描述了错误类型、内存地址以及源文件中发生错误的位置：

   ![ASan 错误消息](media/asan-error.png)

还可以在输出窗口的“调试”窗格中查看完整的 ASan 输出（包括分配/取消分配损坏内存的位置）。

## <a name="enable-asan-for-msbuild-based-linux-projects"></a>为基于 MSBuild 的 Linux 项目启用 ASan

要为基于 MSBuild 的 Linux 项目启用 ASan，请右键单击“解决方案资源管理器”中的项目，然后选择“属性”   。 接下来，导航到“配置属性” > “C/C++” > “擦除器”    。 ASan 通过编译器和链接器标志启用，并且需要重新编译项目才能正常运行。

![为 MSBuild 项目启用 ASan](media/msbuild-asan-prop-page.png)

可通过导航到“配置属性” > “调试” > “AddressSanitizer 运行时标志”，传递可选 ASan 运行时标志    。 单击向下箭头，添加或删除标志。

![配置 ASan 运行时标志](media/msbuild-asan-runtime-flags.png)

## <a name="enable-asan-for-visual-studio-cmake-projects"></a>为 Visual Studio CMake 项目启用 ASan

要为 CMake 启用 ASan，请右键单击“解决方案资源管理器”中的 CMakeLists.txt 文件，然后选择“项目的 CMake 设置”   。

确保在对话框的左侧窗格中选中了 Linux 配置（如“Linux 调试”  ）：

![Linux 调试配置](media/linux-debug-configuration.png)

ASan 选项位于“常规”下  。 以“标志=值”格式输入 ASan 运行时标志，并以分号分隔。

![Linux 调试配置](media/cmake-settings-asan-options.png)

## <a name="install-the-asan-debug-symbols"></a>安装 ASan 调试符号

要启用 ASan 诊断，必须在远程 Linux 计算机或 WSL 安装上安装其调试符号 (libasan-dbg)。 加载的 libasan-dbg 版本取决于 Linux 计算机上安装的 GCC 版本：

|ASan 版本 |GCC 版本 |
| --- | --- |
|libasan0|gcc-4.8|
|libasan2|gcc-5|
|libasan3|gcc-6|
|libasan4|gcc-7|
|libasan5|gcc-8|

可使用以下命令确定拥有的 GCC 版本：

```bash
gcc --version
```

要查看所需的 libasan-dbg 版本，请运行你的程序，然后查看“输出”窗口的“调试”窗格   。 加载的 ASan 版本对应于 Linux 计算机上所需的 libasan-dbg 版本。 可以使用 Ctrl + F 在窗口中搜索“libasan”  。 例如，如果具有 libasan4，则会看到如下所示的行：

```Output
Loaded '/usr/lib/x86_64-linux-gnu/libasan.so.4'. Symbols loaded.
```

可使用以下命令，在使用 apt 的 Linux 发行版上安装 ASan 调试位。 此命令安装版本 4：

```bash
sudo apt-get install libasan4-dbg
```

如果启用了 ASan，Visual Studio 会在“输出”窗口的“调试”窗格顶部提示安装 ASan 调试符号   。

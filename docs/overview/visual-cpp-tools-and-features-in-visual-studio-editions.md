---
title: Visual Studio 版本中的 C++ 工具和功能
ms.date: 05/21/2019
helpviewer_keywords:
- tools and platforms [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: 88eb66440df023254cb806c03a00aa2d71980305
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366795"
---
# <a name="c-tools-and-features-in-visual-studio-editions"></a>Visual Studio 版本中的 C++ 工具和功能

::: moniker range=">=vs-2019"

Visual Studio 2019 中提供以下 C++ 功能。 除非另有说明，否则所有功能均在所有版本中提供：Visual Studio Community、Visual Studio Professional 和 Visual Studio Enterprise。 某些功能需要特定工作负荷或可选组件，可使用 Visual Studio 安装程序进行安装。

## <a name="platforms"></a>平台

- Windows 桌面
- 通用 Windows 平台（平板电脑、PC、Xbox、IoT 和 HoloLens）
- Linux
- Android
- iOS

## <a name="compilers"></a>编译器

- 适用于 x86、x64、ARM 和 ARM64 的 MSVC 32 位编译器
- 适用于 x86、x64、ARM 和 ARM64 的 MSVC 64 位编译器
- 适用于 ARM 的 GCC 跨平台编译器
- Clang/LLVM
  - 在 Windows 上，Clang/LLVM 7.0，面向 x86 或 x64（仅 CMake 支持）。 其他 Clang 版本可能能够正常工作，但不受官方支持。
  - 在 Linux 上，发行版支持的任何 Clang/LLVM 安装。

## <a name="c-workloads"></a>C++ 工作负荷

Visual Studio 包含以下用于 C++ 开发的工作负荷。 可安装其中任意或所有工作负荷，以及其他工作负荷，例如 .NET 桌面开发、Python 开发、Azure 开发、Visual Studio 扩展开发等等。

### <a name="desktop-development-with-c"></a>使用 C++ 的桌面开发

包含：

- C++ 核心桌面功能

可选组件：

- MSVC v142 - VS 2019 C++ x64/x86 生成工具 (v14.21)
- Windows 10 SDK (10.0.17763.0)
- 实时调试器
- C++ 分析工具
- 用于 Windows 的 C++ CMake 工具
- C++ ATL for v142 生成工具（x86 和 x64）
- Boost.Test 测试适配器
- Google Test 测试适配器
- Live Share
- IntelliCode
- IntelliTrace（仅 Enterprise）
- C++ MFC for v142 生成工具（x86 和 x64）
- v142 生成工具的 C++/CLI 支持 (14.21)
- C++ Modules for v142 生成工具（x64/x86 - 试验）
- 适用于 Windows 的 Clang 编译器
- IncrediBuild - 生成加速
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- MSVC v141 - VS 2017 C++ x64/x86 生成工具 (v14.16)
- MSVC v140 - VS 2015 C++ 生成工具 (v14.00)

### <a name="linux-development-with-c"></a>使用 C++ 的 Linux 开发

包含：

- C++ 核心功能
- Windows 通用 C 运行时
- 适用于 Linux 开发的 C++

可选组件：

- 适用于 Linux 的 C++ CMake 工具
- 嵌入式和 IoT 开发工具

### <a name="universal-windows-platform-development"></a>通用 Windows 平台开发

包含：

- Blend for Visual Studio
- .NET 本机和 .NET 标准
- NuGet 程序包管理器
- 通用 Windows 平台工具
- Windows 10 SDK (10.0.17763.0)

可选组件：

- IntelliCode
- IntelliTrace（仅 Enterprise）
- USB 设备连接性
- C++ (v142) 通用 Windows 平台工具
- C++ (v141) 通用 Windows 平台工具
- 适用于 DirectX 的图形调试器和 GPU 探查器
- Windows 10 SDK (10.0.18362.0)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- 体系结构和分析工具

### <a name="c-game-development"></a>C++ 游戏开发

包含：

- C++ 核心功能
- Windows 通用 C 运行时
- C++ 2019 Redistributable 更新
- MSVC v142 - VS 2019 C++ x64/x86 生成工具 (v14.21)

可选组件：

- C++ 分析工具
- Windows 10 SDK (10.0.17763.0)
- IntelliCode
- IntelliTrace（仅 Enterprise）
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- IncrediBuild - 生成加速
- Cocos
- Unreal 引擎安装程序
- 适用于 Unreal 引擎的 Android IDE 支持

### <a name="mobile-development-with-c"></a>使用 C++ 的移动开发

包含：

- C++ 核心功能
- Android SDK 安装（API 级别 25）（使用 C++ 的移动开发的本地安装）

可选组件：

- Android NDK (R16B)
- Apache Ant (1.9.3)
- C++ Android 开发工具
- IntelliCode
- Google Android Emulator（API 级别 25）（本地安装）
- Intel 硬件加速执行管理器 (HAXM)（本地安装）
- Android NDK (R16B)（32 位）
- C++ iOS 开发工具
- IncrediBuild - 生成加速

## <a name="individual-components"></a>各个组件

可独立于任何工作负荷安装这些组件。

- JavaScript 诊断
- Live Share
- 用于 v142 生成工具的 C++ 通用 Windows 平台运行时
- ClickOnce 发布
- Microsoft Visual Studio 安装程序项目

## <a name="libraries-and-headers"></a>库和标头

- Windows 标头和库
- Windows 通用 C 运行时 (CRT)
- C++ 标准库
- ATL
- MFC
- .NET Framework Class Library — .NET Framework 类库
- 针对 .NET 的 C++ 支持库
- OpenMP 2.0
- 通过 vcpkg 目录提供超过 900 个开源库

## <a name="build-and-project-systems"></a>生成和项目系统

- CMake
- 通过 Open Folder 支持任何生成系统
- 命令行生成 (msbuild.exe)
- 本机多目标
- 托管多目标
- 并行生成
- 生成自定义项
- 属性页扩展性

## <a name="project-templates"></a>项目模板

可使用以下项目模板，具体取决于安装的工作负荷。

Windows 桌面：

- 空项目
- 控制台应用
- Windows 桌面向导
- Windows 桌面应用程序
- “共享项”项目
- MFC 应用
- 动态链接库
- CLR 空项目
- CLR 控制台应用
- 静态库
- CMake 项目
- ATL 项目
- MFC 动态链接库
- CLR 类库
- 生成文件项目 (Windows)
- MFC ActiveXControl
- 本机单元测试项目
- Google Test

通用 Windows 平台 (C++/CX)：

- 空白应用程序
- DirectX 11 和 XAML 应用
- DirectX 11 应用
- DirectX 12 应用
- 单元测试应用
- DLL
- Windows 运行时组件
- 静态库
- Windows 应用程序打包项目

Linux：

- 控制台应用 (Linux)
- 空项目 (Linux)
- Raspberry Pi Blink
- 生成文件项目 (Linux)

## <a name="tools"></a>工具

- 增量链接器
- Microsoft 生成文件实用工具 (Nmake.exe)
- Lib 生成器 (Lib.exe)
- Windows 资源编译器 (Rc.exe)
- Windows Resource to Object Converter (CvtRes.exe)
- 浏览信息维护实用工具 (BscMake.exe)
- C++ Name Undecorator (Undname.exe)
- COFF/PE 转储程序 (Dumpbin.exe)
- COFF/PE 编辑器 (Editbin.exe)
- MASM (Ml.exe)
- Spy++
- ErrLook
- AtlTrace
- 推理规则
- 按配置优化

## <a name="debugging-features"></a>调试功能

- 本机调试
- natvis（本机类型可视化）
- 图形调试
- 托管调试
- GPU 使用情况
- 内存使用率
- Remote Debugging
- SQL 调试
- 静态代码分析

## <a name="designers-and-editors"></a>设计器和编辑器

- XAML 设计器
- CSS 样式设计器/编辑器
- HTML 样式设计器/编辑器
- XML 编辑器
- 源代码编辑器
- 提高生产力的功能：重构、EDG IntelliSense 引擎、C++ 代码格式设置
- Windows Forms Designer — Windows 窗体设计器
- 数据设计器
- 本机资源编辑器（.rc 文件）
- 资源编辑器
- 模型编辑器
- 着色器设计器
- 实时依赖项验证（仅 Enterprise）
- 体系结构分层图（仅 Enterprise）
- 体系结构验证（仅 Enterprise）
- 代码克隆（仅 Enterprise）

## <a name="data-features"></a>数据功能

- 数据设计器
- 数据对象
- Web 服务
- 服务器资源管理器

## <a name="automation-and-extensibility"></a>自动化和扩展性

- 扩展性对象模型
- 代码模型
- 项目模型
- 资源编辑器模型
- 向导模型
- 设计器对象模型

## <a name="application-lifecycle-management-tools"></a>Application Lifecycle Management 工具

- 单元测试（Microsoft 本机 C++、Boost.Test、Google Test、CTest）
- 代码图和依赖项关系图（Professional 和 Enterprise）
- 代码覆盖率（仅 Enterprise）
- 手动测试（仅 Enterprise）
- 探索测试（仅 Enterprise）
- 测试用例管理（仅 Enterprise）
- 代码图调试器集成（仅 Enterprise）
- Live Unit Testing（仅 Enterprise）
- IntelliTrace（仅 Enterprise）
- IntelliTest（仅 Enterprise）
- Microsoft Fakes（单元测试隔离）（仅 Enterprise）
- 代码覆盖率（仅 Enterprise）

## <a name="see-also"></a>请参阅

[安装 Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Visual Studio 中的新增功能](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Visual Studio 中的 C++ 项目类型](../build/reference/visual-cpp-project-types.md)

::: moniker-end

::: moniker range="<=vs-2017"

下表显示 Visual Studio 2017 中可用的 Visual C++ 功能。 单元格中的 X 指示功能可用；空单元格指示功能不可用。 括号中的说明指示功能可用，但是受限制。

## <a name="platforms"></a>平台

||||||
|-|-|-|-|-|
|Platform|Visual Studio Express for Windows 10|Visual Studio Express for Windows Desktop|Visual Studio Community/Professional|Visual Studio Enterprise|
|Windows 桌面||X|X|X|
|通用 Windows 平台（手机、平板电脑、PC、Xbox、IoT 和 HoloLens）|X||X|X|
|Linux|X|X|
|Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>编译器

|编译器|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|MSVC 32 位 X86 编译器|X|X|X|X|
|X86_arm 跨平台编译器|X||X|X|
|MSVC 64 位 x64 编译器|||X|X|
|X86_ x64 跨平台编译器|X|X|X|X|

## <a name="libraries-and-headers"></a>库和标头

|库或标头|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Windows 标头和库以及 CRT 库|(X)|X|X|X|
|C++ 标准库|X|X|X|X|
|ATL|||X|X|
|MFC|||X|X|
|.NET Framework Class Library — .NET Framework 类库||X|X|X|
|针对 .NET 的 C++ 支持库||X|X|X|
|OpenMP 2.0|X|X|X|X|

## <a name="project-templates"></a>项目模板

|模板|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|适用于 UWP、Windows 8.1、Windows Phone 8.0 的 XAML 模板|X||X|X|
|Direct3D 应用程序|X||X|X|
|DLL（通用 Windows）|X||X|X|
|静态库（通用 Windows）|X||X|X|
|Windows 运行时组件|X||X|X|
|单元测试应用（通用 Windows）|X||X|X|
|ATL 项目|||X|X|
|类库 (CLR)||X|X|X|
|CLR 控制台应用程序||X|X|X|
|CLR 空项目||X|X|X|
|自定义向导|||X|X|
|空项目||X|X|X|
|生成文件项目||X|X|X|
|MFC ActiveX 控件|||X|X|
|MFC 应用程序|||X|X|
|MFC DLL|||X|X|
|测试项目|X|X|X|X|
|Win32 控制台应用程序||X|X|X|
|Win32 项目||X|X|X|

## <a name="tools"></a>工具

|工具|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|增量链接器|X|X|X|X|
|程序维护实用工具 (Nmake.exe)||X|X|X|
|Lib 生成器 (Lib.exe)|X|X|X|X|
|Windows 资源编译器 (Rc.exe)|X|X|X|X|
|Windows Resource to Object Converter (CvtRes.exe)||X|X|X|
|浏览信息维护实用工具 (BscMake.exe)|X|X|X|X|
|C++ Name Undecorator (Undname.exe)|X|X|X|X|
|COFF/PE 转储程序 (Dumpbin.exe)|X|X|X|X|
|COFF/PE 编辑器 (Editbin.exe)|X|X|X|X|
|MASM (Ml.exe)|||X|X|
|Spy++|||X|X|
|ErrLook|||X|X|
|AtlTrace|||X|X|
|Devenv.com|||X|X|
|推理规则|||X|X|
|将 VCBuild .vcproj 项目升级到 MSBuild (VCUpgrade.exe)|X|X|X|X|
|按配置优化|||X|X|

## <a name="debugging-features"></a>调试功能

|调试功能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|本机调试|X|X|X|X|
|natvis（本机类型可视化）|X|X|X|X|
|图形调试|X||X|X|
|托管调试||X|X|X|
|GPU 使用情况|X||X|X|
|内存使用率|X||X|X|
|Remote Debugging|X|X|X|X|
|SQL 调试|||X|X|
|静态代码分析|有限|有限|X|X|

## <a name="designers-and-editors"></a>设计器和编辑器

|设计器或编辑器|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|XAML 设计器|X||X|X|
|CSS 样式设计器/编辑器|X|X|X|X|
|HTML 样式设计器/编辑器|X|X|X|X|
|XML 编辑器|X|X|X|X|
|源代码编辑器|X|X|X|X|
|提高生产力的功能：重构、IntelliSense、C++ 代码格式设置|X|X|X|X|
|Windows Forms Designer — Windows 窗体设计器||X|X|X|
|数据设计器|||X|X|
|本机资源编辑器（.rc 文件）|||X|X|
|资源编辑器|X|X|X|X|
|模型编辑器|X||X|X|
|着色器设计器|X||X|X|

## <a name="data-features"></a>数据功能

|数据功能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|数据设计器|||X|X|
|数据对象|||X|X|
|Web 服务|||X|X|
|服务器资源管理器|||X|X|

## <a name="build-and-project-systems"></a>生成和项目系统

|生成或项目功能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|命令行生成 (msbuild.exe)|X|X|X|X|
|本机多目标||X|X|X|
|托管多目标||X|X|X|
|并行生成|X|X|X|X|
|生成自定义项|X|X|X|X|
|属性页扩展性|X|X|X|X|

## <a name="automation-and-extensibility"></a>自动化和扩展性

|自动化和扩展性|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|扩展性对象模型|||X|X|
|代码模型|||X|X|
|项目模型|||X|X|
|资源编辑器模型|||X|X|
|向导模型|||X|X|
|设计器对象模型|||X|X|

## <a name="application-lifecycle-management-tools"></a>Application Lifecycle Management 工具

||||||
|-|-|-|-|-|
|工具|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|单元测试（本机框架）|X|X|X|X|
|单元测试（托管框架）||X|X|X|
|代码覆盖率||||X|
|手动测试||||X|
|探索测试||||X|
|测试用例管理||||X|
|代码图和依赖项关系图|||只读|X|
|代码图调试||||X|

## <a name="see-also"></a>请参阅

[安装 Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Visual Studio 中的新增功能](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Visual Studio 中的 C++ 项目类型](../build/reference/visual-cpp-project-types.md)

::: moniker-end

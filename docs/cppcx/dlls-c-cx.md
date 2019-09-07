---
title: DLL (C++/CX)
ms.date: 02/06/2018
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
ms.openlocfilehash: 4db0ed4f11f03c65c440c7b654653347da1d4536
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740260"
---
# <a name="dlls-ccx"></a>DLL (C++/CX)

可以使用 Visual Studio 创建可供通用 Windows 平台（UWP）应用使用的标准 Win32 DLL 或 Windows 运行时组件 DLL。 使用 Visual Studio 版本或早于 Visual Studio 2012 的 Microsoft C++编译器创建的标准 DLL 可能无法在 UWP 应用中正确加载，并且可能不会在 Microsoft Store 中通过应用验证测试。

## <a name="windows-runtime-component-dlls"></a>Windows 运行时组件 Dll

几乎在所有情况下，当你想要创建在 UWP 应用程序中使用的 DLL 时，可以使用该名称的项目模板将其创建为 Windows 运行时组件。 可以为具有公共或私有 Windows 运行时类型的 Dll 创建 Windows 运行时组件项目。 可以从以任何 Windows 运行时兼容语言编写的应用程序访问 Windows 运行时组件。 默认情况下，Windows 运行时组件项目的编译器设置使用 **/ZW**开关。 .winmd 文件必须具有和根命名空间相同的名称。 例如，名为 A.B.C.MyClass 的类只有在名为 A.winmd 或 A.B.winmd 或 A.B.C.winmd 的元数据文件中定义后才能实例化。 DLL 的名称不必与 .winmd 文件名匹配。

有关详细信息，请参阅 [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>在项目中引用第三方 Windows 运行时组件二进制文件

1. 打开将要使用该 DLL 的项目的快捷菜单，然后选择 **“属性”** 。 在 **“公共属性”** 页上，选择 **“添加新引用”** 按钮。

1. Windows 运行时组件包含一个 DLL 文件和一个包含元数据的 winmd 文件。 通常，这些文件位于同一文件夹中。 在 **“添加引用”** 对话框的左窗格中，选择 **“浏览”** 按钮，然后定位到该 DLL 及其 .winmd 文件的位置。 有关详细信息，请参阅[扩展 sdk](/visualstudio/extensibility/creating-a-software-development-kit#extension-sdks)。

## <a name="standard-dlls"></a>标准 DLL

可以为C++不使用或生成公共 Windows 运行时类型的代码创建标准 DLL，并将其从 UWP 应用中使用。 当你只想迁移现有 DLL 以便在此版本的 Visual Studio 中进行编译，但不将代码转换为 Windows 运行时组件项目时，请使用动态链接库（DLL）项目类型。 在使用下列步骤时，将在 .appx 包中的应用程序可执行文件旁边部署 DLL。

### <a name="to-create-a-standard-dll-in-visual-studio"></a>在 Visual Studio 中创建标准 DLL

1. 在菜单栏上，依次选择 "**文件**"、"**新建**"、"**项目**"，然后选择 "**动态链接库（DLL）** " 模板。

1. 输入项目名称，然后选择 **“确定”** 按钮。

1. 添加代码。 确保将 `__declspec(dllexport)` 用于你准备导出的函数，例如 `__declspec(dllexport) Add(int I, in j);`

1. 添加`#include winapifamily.h`以将该标头文件包含在 UWP 应用的 Windows SDK 中，并`WINAPI_FAMILY=WINAPI_PARTITION_APP`设置宏。

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>从同一解决方案引用标准 DLL 项目

1. 打开将要使用该 DLL 的项目的快捷菜单，然后选择 **“属性”** 。 在 **“公共属性”** 页上，选择 **“添加新引用”** 按钮。

1. 在左窗格中，选择 **“解决方案”** ，然后在右窗格中选中相应的复选框。

1. 在源代码文件中，根据需要为 DLL 标头文件添加 `#include` 语句。

### <a name="to-reference-a-standard-dll-binary"></a>引用标准 DLL 二进制文件

1. 复制 DLL 文件、.lib 文件和标头文件，将它们粘贴到一个已知位置（如你的当前项目文件夹中）。

1. 打开将要使用该 DLL 的项目的快捷菜单，然后选择 **“属性”** 。 在 **“配置属性”** &gt; **“链接器”** &gt; **“输入”** 页上，添加 .lib 文件作为依赖项。

1. 在源代码文件中，根据需要为 DLL 标头文件添加 `#include` 语句。

### <a name="to-migrate-an-existing-win32-dll-for-uwp-app-compatibility"></a>为 UWP 应用兼容性迁移现有 Win32 DLL

1. 创建 DLL （通用 Windows）类型的项目，并将现有源代码添加到其中。

1. 添加`#include winapifamily.h`以将该标头文件包含在 UWP 应用的 Windows SDK 中，并`WINAPI_FAMILY=WINAPI_PARTITION_APP`设置宏。

1. 在源代码文件中，根据需要为 DLL 标头文件添加 `#include` 语句。

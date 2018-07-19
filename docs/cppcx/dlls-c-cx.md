---
title: Dll (C + + /cli CX) |Microsoft 文档
ms.custom: ''
ms.date: 02/06/2018
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 39c334c659980dccdca670ab91501f0e30c4e6d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088084"
---
# <a name="dlls-ccx"></a>DLL (C++/CX)

Visual Studio 可用于创建标准 Win32 DLL 或 Windows 运行时组件可供通用 Windows 平台 (UWP) 应用的 DLL。 通过使用 Visual Studio 或早于 Visual Studio 2012 中的 UWP 应用可能无法正确加载和在 Microsoft 应用商店中可能无法通过此应用程序验证测试的 Visual c + + 编译器的版本创建标准 DLL。

## <a name="windows-runtime-component-dlls"></a>Windows 运行时组件 Dll

在几乎所有情况下，当你想要创建的 DLL 时，在 UWP 应用中使用，通过该名称的项目模板创建为 Windows 运行时组件。 你可以为具有公共或私有 Windows 运行时类型的 Dll 创建 Windows 运行时组件项目。 可以从任何 Windows 运行时兼容语言编写的应用程序访问的 Windows 运行时组件。 默认情况下，Windows 运行时组件的编译器设置项目使用 **/ZW**切换。 .winmd 文件必须具有和根命名空间相同的名称。 例如，名为 A.B.C.MyClass 的类只有在名为 A.winmd 或 A.B.winmd 或 A.B.C.winmd 的元数据文件中定义后才能实例化。 DLL 的名称不必与 .winmd 文件名匹配。

有关详细信息，请参阅[创建 Windows 运行时 c + + 组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>若要引用二进制项目中的第三方 Windows 运行时组件

1. 打开将要使用该 DLL 的项目的快捷菜单，然后选择 **“属性”**。 在 **“公共属性”** 页上，选择 **“添加新引用”** 按钮。

1. Windows 运行时组件由 DLL 文件和包含的元数据的.winmd 文件组成。 通常，这些文件位于同一文件夹中。 在 **“添加引用”** 对话框的左窗格中，选择 **“浏览”** 按钮，然后定位到该 DLL 及其 .winmd 文件的位置。 有关详细信息，请参阅[扩展 Sdk](/visualstudio/extensibility/creating-a-software-development-kit#ExtensionSDKs)。

## <a name="standard-dlls"></a>标准 DLL

你可以创建的标准 DLL 时，不使用或生成公共 Windows 运行时类型和使用它从 UWP 应用的 c + + 代码。 如果你只希望迁移要在此版本的 Visual Studio 中编译而不是将代码转换为 Windows 运行时组件项目的现有 DLL，使用动态链接库 (DLL) 项目类型。 在使用下列步骤时，将在 .appx 包中的应用程序可执行文件旁边部署 DLL。

### <a name="to-create-a-standard-dll-in-visual-studio"></a>在 Visual Studio 中创建标准 DLL

1. 在菜单栏上，选择**文件**，**新建**，**项目**，然后选择**动态链接库 (DLL)** 模板。

1. 输入项目名称，然后选择 **“确定”** 按钮。

1. 添加代码。 确保将 `__declspec(dllexport)` 用于你准备导出的函数，例如 `__declspec(dllexport) Add(int I, in j);`

1. 添加`#include winapifamily.h`包括适用于 UWP 应用的 Windows SDK 中该标头文件并设置宏`WINAPI_FAMILY=WINAPI_PARTITION_APP`。

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>从同一解决方案引用标准 DLL 项目

1. 打开将要使用该 DLL 的项目的快捷菜单，然后选择 **“属性”**。 在 **“公共属性”** 页上，选择 **“添加新引用”** 按钮。

1. 在左窗格中，选择 **“解决方案”**，然后在右窗格中选中相应的复选框。

1. 在源代码文件中，根据需要为 DLL 标头文件添加 `#include` 语句。

### <a name="to-reference-a-standard-dll-binary"></a>引用标准 DLL 二进制文件

1. 复制 DLL 文件、.lib 文件和标头文件，将它们粘贴到一个已知位置（如你的当前项目文件夹中）。

1. 打开将要使用该 DLL 的项目的快捷菜单，然后选择 **“属性”**。 在 **“配置属性”**&gt; **“链接器”**&gt; **“输入”** 页上，添加 .lib 文件作为依赖项。

1. 在源代码文件中，根据需要为 DLL 标头文件添加 `#include` 语句。

### <a name="to-migrate-an-existing-win32-dll-for-uwp-app-compatibility"></a>若要迁移现有 Win32 DLL 以实现 UWP 应用程序兼容性

1. 创建 DLL (通用 Windows) 类型的项目并向其添加你现有的源代码。

1. 添加`#include winapifamily.h`包括适用于 UWP 应用的 Windows SDK 中该标头文件并设置宏`WINAPI_FAMILY=WINAPI_PARTITION_APP`。

1. 在源代码文件中，根据需要为 DLL 标头文件添加 `#include` 语句。

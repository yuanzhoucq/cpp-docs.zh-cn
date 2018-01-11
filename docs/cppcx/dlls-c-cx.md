---
title: "Dll (C + + /cli CX) |Microsoft 文档"
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
caps.latest.revision: "21"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a759541dd31121f12283f9b2b0c5b468da477554
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dlls-ccx"></a>DLL (C++/CX)
Visual Studio 可用于创建标准 Win32 DLL 或 Windows 运行时组件可由通用 Windows 平台应用程序使用的 DLL。 通过使用 Visual Studio 或早于 Visual Studio 2012 可能不会在通用 Windows 平台应用程序中正确加载和可能无法通过在此应用程序验证测试的 Visual c + + 编译器的版本创建的标准 DLL [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)]。  
  
## <a name="windows-runtime-component-dlls"></a>Windows 运行时组件 Dll  
 在几乎所有情况下，当你想要在通用 Windows 平台应用中创建的 DLL 时，使用，它为 Windows 运行时组件通过创建该名称的项目模板。 你可以为具有公共或私有 Windows 运行时类型的 Dll 创建 Windows 运行时组件项目。 可以从任何 Windows 运行时兼容语言编写的应用程序访问的 Windows 运行时组件。 默认情况下，Windows 运行时组件的编译器设置项目使用**/ZW**切换。 .winmd 文件必须具有和根命名空间相同的名称。 例如，名为 A.B.C.MyClass 的类只有在名为 A.winmd 或 A.B.winmd 或 A.B.C.winmd 的元数据文件中定义后才能实例化。 DLL 的名称不必与 .winmd 文件名匹配。  
  
 有关详细信息，请参阅 [Creating Windows Runtime Components in C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md)。  
  
#### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>若要引用二进制项目中的第三方 Windows 运行时组件  
  
1.  打开将要使用该 DLL 的项目的快捷菜单，然后选择 **“属性”**。 在 **“公共属性”** 页上，选择 **“添加新引用”** 按钮。  
  
2.  Windows 运行时组件由 DLL 文件和包含的元数据的.winmd 文件组成。 通常，这些文件位于同一文件夹中。 在 **“添加引用”** 对话框的左窗格中，选择 **“浏览”** 按钮，然后定位到该 DLL 及其 .winmd 文件的位置。 有关更多信息，请参见 [教程：创建和使用扩展 SDK](http://msdn.microsoft.com/en-us/001e2fca-3d56-43ab-a5e0-0561d085679f)。  
  
## <a name="standard-dlls"></a>标准 DLL  
 你可以创建的标准 DLL 时，不使用或生成公共 Windows 运行时类型和从通用 Windows 平台应用中使用它的 c + + 代码。 当你只希望迁移要在此版本的 Visual Studio 中编译而不是将代码转换为 Windows 运行时组件项目的现有 DLL 时，请使用通用 Windows 平台 DLL 项目类型。 在使用下列步骤时，将在 .appx 包中的应用程序可执行文件旁边部署 DLL。  
  
#### <a name="to-create-a-standard-dll-in-visual-studio"></a>在 Visual Studio 中创建标准 DLL  
  
1.  在菜单栏上，选择**文件**，**新建**，**项目**，然后选择通用 Windows 平台 DLL 模板。  
  
2.  输入项目名称，然后选择 **“确定”** 按钮。  
  
3.  添加代码。 确保将 `__declspec(dllexport)` 用于你准备导出的函数，例如 `__declspec(dllexport) Add(int I, in j);`  
  
4.  添加`#include winapifamily.h`包括 Windows SDK 中的通用 Windows 平台应用该标头文件并设置宏`WINAPI_FAMILY=WINAPI_PARTITION_APP`。  
  
#### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>从同一解决方案引用标准 DLL 项目  
  
1.  打开将要使用该 DLL 的项目的快捷菜单，然后选择 **“属性”**。 在 **“公共属性”** 页上，选择 **“添加新引用”** 按钮。  
  
2.  在左窗格中，选择 **“解决方案”**，然后在右窗格中选中相应的复选框。  
  
3.  在源代码文件中，根据需要为 DLL 标头文件添加 `#include` 语句。  
  
#### <a name="to-reference-a-standard-dll-binary"></a>引用标准 DLL 二进制文件  
  
1.  复制 DLL 文件、.lib 文件和标头文件，将它们粘贴到一个已知位置（如你的当前项目文件夹中）。  
  
2.  打开将要使用该 DLL 的项目的快捷菜单，然后选择 **“属性”**。 在 **“配置属性”**&gt; **“链接器”**&gt; **“输入”** 页上，添加 .lib 文件作为依赖项。  
  
3.  在源代码文件中，根据需要为 DLL 标头文件添加 `#include` 语句。  
  
#### <a name="to-migrate-an-existing-win32-dll-for-universal-windows-platform-app-compatibility"></a>若要迁移现有 Win32 DLL 以实现通用 Windows 平台应用程序兼容性  
  
1.  创建通用 Windows 平台 DLL 类型的项目并向其添加你现有的源代码。  
  
2.  添加`#include winapifamily.h`包括 Windows SDK 中的通用 Windows 平台应用该标头文件并设置宏`WINAPI_FAMILY=WINAPI_PARTITION_APP`。  
  
3.  在源代码文件中，根据需要为 DLL 标头文件添加 `#include` 语句。  
  


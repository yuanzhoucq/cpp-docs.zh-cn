---
title: 如何：在通用 Windows 平台应用中使用现有 C++ 代码
ms.date: 04/08/2019
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
ms.openlocfilehash: 3aeef205effe072a25fc0b3dabb9145245461d45
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59424191"
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>如何：在通用 Windows 平台应用中使用现有 C++ 代码

要在通用 Windows 平台 (UWP) 环境中运行桌面程序，最简单的方法或许是使用桌面桥技术。 这包括 Desktop App Converter，它能将现有应用程序打包为 UWP 应用，而无需更改代码。 有关详细信息，请参阅[桌面桥](/windows/uwp/porting/desktop-to-uwp-root)。

本主题的剩余部分讨论如何将 C++ 库（DLL 和静态库）移植到通用 Windows 平台。 可能需要执行此操作，以便将核心 C++ 逻辑用于多个 UWP 应用。

UWP 应用在受保护的环境中运行，结果，很多可能危及平台安全的 Win32、COM 和 CRT API 调用都不被允许。 如果使用 `/ZW` 选项，则编译器可以检测此类调用并生成错误。 你可以使用应用程序上的应用认证工具包检测调用禁止的 API 的代码。 有关详细信息，请参见 [Windows 应用认证工具包](/windows/uwp/debug-test-perf/windows-app-certification-kit)。

如果源代码可用于库，则你可能能够消除禁止的 API 调用。 有关详细信息（包括允许或禁止的 API 的列表），请参阅[用于 UWP 应用的 Win32 和 COM API](/uwp/win32-and-com/win32-and-com-for-uwp-apps) 以及[通用 Windows 平台应用中不支持的 CRT 函数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。 可通过 [UWP 应用中的 Windows API 替代项](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)，找到一些替代项。

如果只是尝试从通用 Windows 项目添加引用到经典桌面库，你将得到一条显示库不兼容的错误消息。 如果是静态库，你只需通过将库（.lib 文件）添加到链接器输入就可以链接到库，类似在经典 Win32 应用程序中的操作。 对于仅二进制可用的库，这是唯一的选项。 静态库链接到应用的可执行文件中，但在 UWP 应用中使用的 Win32 DLL 必须通过将其包括在项目中并标记为“内容”来打包到应用中。 要在 UWP 应用中加载 Win32 DLL，还需要调用 [LoadPackagedLibrary](/windows/desktop/api/winbase/nf-winbase-loadpackagedlibrary)，而不是 `LoadLibrary` 或 `LoadLibraryEx`。

如果你有 DLL 或静态库的源代码，可使用 `/ZW` 重新编译为 UWP 项目。 如果要这样做，可使用解决方案资源管理器添加引用并在 C++ UWP 应用中使用它。 在 DLL 的情况下，与导出库链接。

若要向其他语言中的调用方公开功能，则可以将库转换为 Windows 运行时组件。 Windows 运行时组件与普通的 DLL 的不同之处在于它们包括 .winmd 文件格式的元数据，这些元数据以 .NET 和 JavaScript 的使用者需要的方式介绍内容。 若要向其他语言公开 API 元素，你可以添加 C++/CX 构造（如 ref 类）并将其设置为公共，或使用 [Windows 运行时 C++ 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。  在 Windows 10 以及更高版本中，可使用 [C++/WinRT 库](https://github.com/microsoft/cppwinrt)，而不是 C++/CX。

前面的讨论不适用于 COM 组件案例，COM 组件必须以不同方式处理。 如果在 EXE 或 DLL 中具有 COM 服务器，只要将其作为[免注册 COM 组件](/windows/desktop/sbscs/creating-registration-free-com-objects)打包，将其作为内容文件添加到你的项目，并使用 [CoCreateInstanceFromApp](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstancefromapp) 将其实例化，就可以在通用 Windows 项目中使用它。 有关详细信息，请参阅[在 Windows 应用商店 C++ 项目中使用 Free-COM DLL](https://blogs.msdn.microsoft.com/win8devsupport/2013/05/19/using-free-com-dll-in-windows-store-c-project/)。

如果想要将现有 COM 库移植到 UWP，可通过使用 [Windows 运行时 C++ 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md) 将其转换为 Windows 运行时组件。 WRL 不支持 ATL 和 OLE的所有功能，因此这种端口是否可行取决于 COM 代码多少，取决于你的组件需要 COM、ATL 以及 OLE 的哪些功能。

这些是你可以在 UWP 项目中使用现有的 C++ 代码的各种方法。 某些方法不需要在组件扩展 (C++/CX) 启用（即使用 `/ZW` 选项）的情况下对代码重新编译，而某些方法需要。因此如果你需要在标准 C++ 中保存代码，或者为某些代码保留经典的 Win32 编译环境，则可重新编译并选择相应的体系结构。 例如，所有包含 UWP 用户界面的代码和要向 C#、Visual Basic 和 JavaScript 调用方公开的类型都应存在于 Windows 应用项目和 Windows 运行时组件项目中。 只需要在 C++（包括 C++/CX）代码中使用的代码可存在于使用 `/WX` 选项编译的项目中或标准 C++ 项目中。 仅当仅二进制代码不使用禁止的 API 时，可通过将其作为静态库链接，或作为内容与应用一起打包并在 DLL 中加载来使用。

无论选择哪种开发方案，都应注意可以在代码中使用一些宏定义，以便可以在经典桌面 Win32 和 UWP 下有条件地编译代码。

```cpp
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
```

这些语句分别适用于 UWP 应用、Windows Phone 应用商店应用、都适用或都不适用（仅针对经典 Win32 桌面）。 这些宏仅在 Windows SDK 8.1 及更高版本中才可用，因此如果你的代码需要使用早期版本的 Windows SDK 或除 Windows 以外的其他平台进行编译，则还应考虑未定义它们中任何一个这种情况。

本主题包含下列过程：

- [在 UWP 应用中使用 Win32 DLL](#BK_Win32DLL)

- [在 UWP 应用中使用本机 C++ 静态库](#BK_StaticLib)

- [将 C++ 库移植到 Windows 运行时组件](#BK_WinRTComponent)

##  <a name="BK_Win32DLL"></a>在 UWP 应用中使用 Win32 DLL

为了获得更好的安全性和可靠性，通用 Windows 应用在受限的运行时环境中运行，因此不能像在经典 Windows 桌面应用程序中那样使用任何本机 DLL。 如果你有 DLL 的源代码，则可以移植此代码，以便使其在 UWP 上运行。 你首先更改几个项目设置和项目文件元数据，以将此项目标识为 UWP 项目。 你需要使用 `/ZW` 选项编译库代码，从而启用 C++/CX。 由于与该环境相关的控制更严格，在 UWP 应用中，某些 API 调用是不被允许的。 请参阅[用于 UWP 应用的 Win32 和 COM API](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。

如果你的本机 DLL 使用 `__declspec(dllexport)` 公开函数，则可使用以下过程。

### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>若要在无需创建新项目的情况下将本机 DLL 移植到 UWP

1. 如果你的本机 DLL 使用 `__declspec(dllexport)` 导出函数，则可以通过将 DLL 重新编译为 UWP 项目，从 UWP 应用中调用这些函数。 例如，假设我们有一个 DLL，它使用类似于以下标头文件的代码，可导出几个类及其方法：

    ```cpp
    // giraffe.h
    #pragma once

    #ifdef _DLL
    #define GIRAFFE_API __declspec(dllexport)
    #else
    #define GIRAFFE_API
    #endif

    GIRAFFE_API int giraffeFunction();

    class Giraffe
    {
        int id;
            Giraffe(int id_in);
        friend class GiraffeFactory;

    public:
        GIRAFFE_API int GetID();
    };

    class GiraffeFactory
    {
        static int nextID;

    public:
        GIRAFFE_API GiraffeFactory();
        GIRAFFE_API static int GetNextID();
        GIRAFFE_API static Giraffe* Create();
    };
    ```

   以下代码文件：

    ```cpp
    // giraffe.cpp
    #include "stdafx.h"
    #include "giraffe.h"

    Giraffe::Giraffe(int id_in) : id(id_in)
    {
    }

    int Giraffe::GetID()
    {
      return id;
    }

    int GiraffeFactory::nextID = 0;

    GiraffeFactory::GiraffeFactory()
    {
        nextID = 0;
    }

    int GiraffeFactory::GetNextID()
    {
        return nextID;
    }

    Giraffe* GiraffeFactory::Create()
    {
        return new Giraffe(nextID++);
    }

    int giraffeFunction();
    ```

   项目（stdafx.h、dllmain.cpp）中的其他所有内容都属于标准 Win32 项目模板。 如果想要遵循这些步骤，但又不想将自己的 DLL 用于这些步骤，请尝试创建 Win32 项目，在项目向导中选择 DLL，然后添加标头文件 giraffe.h 和代码文件 giraffe.cpp，并在此步骤中，将代码中的内容复制到相应的文件中。

   该代码将在定义 `_DLL` 时（即当项目生成为 DLL 时），定义解析为 `__declspec(dllexport)` 的宏 `GIRAFFE_API`。

2. 打开 DLL 项目中的“项目属性”，并将“配置”设置为“所有配置”。

3. 在“项目属性”的“C/C++” > “常规”选项卡下，将“使用 Windows 运行时扩展”设置为“是(/ZW)”。 这将启用组件扩展 (C++/CX)。

4. 在“解决方案资源管理器”中，选择项目节点，打开快捷菜单，然后选择“卸载项目”。 然后，在卸载的项目节点上打开快捷菜单，然后选择编辑项目文件。 找到 `WindowsTargetPlatformVersion` 元素，并将其替换为下列元素。

    ```xml
    <AppContainerApplication>true</AppContainerApplication>
    <ApplicationType>Windows Store</ApplicationType>
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
    ```

   关闭 .vcxproj 文件，再次打开快捷菜单，然后选择“重新加载项目”。

   现在，解决方案资源管理器会将该项目标识为通用 Windows 项目。

5. 请确保预编译的头文件的名称正确。 在“预编译标头”部分中，将预编译头文件从 pch.h 更改为 stdafx.h。 如果没有这样操作，将出现以下错误。

   > 错误 C2857：在源文件中没有找到用 /Ycpch.h 命令行选项指定的“#include”语句

   问题在于通用 Windows 项目对预编译标头文件使用不同的命名约定。

6. 生成项目。 可能会收到一些有关不兼容的命令行选项的错误。 例如，许多较旧的 C++ 项目中默认设置有“启用最小重新生成(/Gm)”这一常用选项（但现在已弃用），它与 `/ZW` 不兼容。

   当为通用 Windows 平台编译时，某些功能不可用。 将看到有关任何问题的编译器错误。 解决这些问题，直到有一个干净的生成。

7. 要在同一解决方案中的 UWP 应用中使用该 DLL，请打开 UWP 项目节点的快捷菜单，然后选择“添加” > “引用”。

   在“项目” > “解决方案”下，选中 DLL 项目旁边的复选框，然后选择“确定”按钮。

8. 将库的标头文件包含在 UWP 应用的 pch.h 文件中。

    ```cpp
    #include "..\MyNativeDLL\giraffe.h"
    ```

9. 照常将代码添加到 UWP 项目中，以从 DLL 中调用函数并创建类型。

    ```cpp
    MainPage::MainPage()
    {
        InitializeComponent();
        GiraffeFactory gf;
        Giraffe* g = gf.Create();
        int id = g->GetID();
    }
    ```

##  <a name="BK_StaticLib"></a>在 UWP 应用中使用本机 C++ 静态库

你可以在 UWP 项目中使用本机 C++ 静态库，但有一些限制和局限需要注意。 请先阅读 [C++/CX 中的静态库](../cppcx/static-libraries-c-cx.md)。 你可以从 UWP 应用访问静态库中的本机代码，但不建议在此类静态库中创建公共 ref 类型。 如果使用 `/ZW` 选项编译静态库，则管理员（实际是经过伪装的链接器）会发出警告：

> LNK4264: 正在将使用 /ZW 编译的对象文件归档到静态库中；请注意，创作 Windows 运行时类型时，建议不要与包含 Windows 运行时元数据的静态库链接

但是，无需使用 `/ZW` 重新编译 UWP 中的静态库即可使用该库。 你将无法声明任何 ref 类型或使用 C++/CX 构造，但如果你的目的仅仅是使用本机代码的库，则可以通过执行以下步骤来执行此操作。

### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>若要在 UWP 项目中使用本机 C++ 静态库

1. 在 UWP 项目的项目属性中，访问“链接器”部分，在输入属性中将路径添加到库。 例如，对于将其输出放置在 *SolutionFolder*\Debug\MyNativeLibrary\MyNativeLibrary.lib 中的项目中的库，则添加相对路径 `Debug\MyNativeLibrary\MyNativeLibrary.lib`。

2. 添加一个 include 语句以对 UWP 项目中的 pch.h 引用头文件，并开始添加使用库的代码。

   ```cpp
   #include "..\MyNativeLibrary\giraffe.h"
   ```

   不要在“解决方案资源管理器”的“引用”节点中添加引用 。 该机制仅适用于 Windows 运行时组件。

##  <a name="BK_WinRTComponent"></a>将 C++ 库移植到 Windows 运行时组件

如果你想要从 UWP 应用使用静态库中的本机 API，并且你具有本机库的源代码，则你可以将代码移植到 Windows 运行时组件。 它将不再是静态库，而将是 DLL。 你可以在任何 C++ UWP 应用中使用它，但与静态库不同，你可以无论何种语言，都能够添加 ref 类型和可用于 UWP 应用代码中的客户端的其他 C++/CX 构造。 因此，你可以从 C#、Visual Basic 或 JavaScript 来访问这些类型。  基本过程如下：创建 Windows 运行时组件项目，将静态库的代码复制到其中，再解决将代码从标准的 C++ 编译移至 `/ZW` 编译而引发的所有错误。

### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>若要将 C++ 库移植到 Windows 运行时组件

1. 创建 Windows 运行时组件项目。

2. 关闭该项目。

3. 在 Windows 文件资源管理器中，找到该项目。 默认情况下，Visual Studio 将使用“文档”文件夹中的“Visual Studio 2017”\“项目”文件夹。 找到 C++ 库项目，该项目包含你想要移植的代码。 从 C++ 库项目复制源文件（头文件、代码文件和包括在子目录中的任何其他资源），并将它们粘贴到项目文件夹，同时确保保留相同的文件夹结构。

4. 重新打开 Windows 运行时组件项目，并在解决方案资源管理器中打开项目节点的快捷菜单，然后选择“添加” > “现有项”。

5. 从原始项目中选择要添加的所有文件，然后选择“确定”。 如果子文件夹需要，则重复。

6. 你现在可能有一些重复代码。 如果你有多个预编译的标头（假设 stdafx.h 和 pch.h），选择一个保留。 将任何所需的代码（比如 include 语句）复制到你要保留的标头中。 然后，删除另一个，并在“预编译标头”下的项目属性中，请确保头文件的名称正确。

   如果更改了要用作预编译标头的文件，请确保预编译标头选项适用于每个文件。 依次选择每个 .cpp 文件，打开其属性窗口，并确保所有项都设置为“使用 (/Yu)”（所需的预编译标头除外，其应设置为“创建 (/Yc)”）。

7. 生成项目并解决任何错误。 这些错误可能由使用 `/ZW` 选项导致，可能由新版本的 Windows SDK 导致，也可能反映了依赖关系（例如，你的库依赖的头文件或新旧项目之间的项目设置差异）。

8. 将公共 ref 类型添加到你的项目，或将普通类型转换为 ref 类型，以便于在想要从 UWP 应用调用的功能中公开入口点。

9. 通过从 UWP 应用项目添加对组件的引用来测试该组件，然后添加某些代码来调用你创建的公共 API。

## <a name="see-also"></a>请参阅

[移植到通用 Windows 平台](../porting/porting-to-the-universal-windows-platform-cpp.md)

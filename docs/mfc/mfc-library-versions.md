---
title: MFC 库版本
ms.date: 05/08/2019
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
ms.openlocfilehash: bf10d8b56f82714fa708b5409923e765206eb16d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626134"
---
# <a name="mfc-library-versions"></a>MFC 库版本

MFC 库可用于支持 ANSI 单字节和多字节字符集（MBCS）代码的版本，以及支持 Unicode 的版本（编码为 UTF-16LE，即 Windows native 字符集）。 每个 MFC 版本都作为静态库或共享 DLL 提供。 还有一个较小的 MFC 静态库版本，它为对大小非常敏感且不需要这些控件的应用程序留下了用于对话框的 MFC 控件。 对于支持的体系结构（包括 x86、x64 和 ARM 处理器），MFC 库在调试和发布版本中均可用。 你可以创建应用程序（.exe 文件）和具有任意版本的 MFC 库的 Dll。 还提供了一组用于与托管代码进行交互的 MFC 库。 MFC 共享 Dll 包含一个版本号，用于指示库的二进制文件兼容性。

## <a name="automatic-linking-of-mfc-library-versions"></a>自动链接 MFC 库版本

MFC 头文件基于生成环境中定义的值自动确定要链接的 MFC 库的正确版本。 MFC 头文件添加编译器指令，指示链接器链接到特定版本的 MFC 库。

例如，AFX。H 头文件指示链接器链接到 MFC 的完全静态、受限静态或共享 DLL 版本中;ANSI/MBCS 或 Unicode 版本;调试或零售版本，具体取决于您的生成配置：

```cpp
#ifndef _AFXDLL
    #ifdef _AFX_NO_MFC_CONTROLS_IN_DIALOGS
        #ifdef _DEBUG
            #pragma comment(lib, "afxnmcdd.lib")
        #else
            #pragma comment(lib, "afxnmcd.lib")
        #endif
        #pragma comment(linker, "/include:__afxNoMFCControlSupportInDialogs")
        #pragma comment(linker, "/include:__afxNoMFCControlContainerInDialogs")
    #endif
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "nafxcwd.lib")
        #else
            #pragma comment(lib, "nafxcw.lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "uafxcwd.lib")
        #else
            #pragma comment(lib, "uafxcw.lib")
        #endif
    #endif
#else
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "d.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "d.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER ".lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER ".lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "ud.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "ud.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "u.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "u.lib")
        #endif
    #endif
#endif
```

MFC 头文件还包括用于在所有所需的库中链接的指令，包括 MFC 库、Win32 库、OLE 库、从示例生成的 OLE 库、ODBC 库等。

## <a name="ansi-mbcs-and-unicode"></a>ANSI、MBCS 和 Unicode

MFC ANSI/MBCS 库版本支持单字节字符集，例如 ASCII 和多字节字符集，如 shift-jis。 MFC Unicode 库版本支持采用 UTF-16LE 宽字符编码形式的 Unicode。 使用 MFC 的 ANSI/MBCS 库版本实现 UTF-8 编码的 Unicode 支持。

若要将项目配置设置为在 IDE 中使用单字节、多字节或宽字符 Unicode 字符串和字符支持，请使用 "**项目属性**" 对话框。 在 "**配置属性**" "  >  **常规**" 页中，将 "**字符集**" 属性设置为 "**不**使用单字节字符集"。 将属性设置为**使用多字节**字符集，以使用多字节字符集，或**使用 Unicode 字符集**将 unicode 编码为 utf-16。

MFC 项目使用预处理器符号 \_ unicode 指示 utf-16 宽字符 unicode 支持，并使用 \_ MBCS 指示 mbcs 支持。 在项目中，这些选项是互斥的。

## <a name="mfc-static-library-naming-conventions"></a>MFC 静态库命名约定

MFC 的静态库使用以下命名约定。 库名采用以下格式

> <em>u</em>AFX<em>cd</em>。LIB

其中，使用斜体小写字母形式显示的字母是说明符的占位符，下表中显示了说明符的含义：

|说明符|值和含义|
|---------------|-------------------------|
|*u*|ANSI/MBCS （N）或 Unicode （U）;在对话框中省略没有 MFC 控件的版本|
|*ansi-c*|对话框中包含 MFC 控件的版本（CW）或不包含（NMCD）|
|*d*|调试或发布：D 表示调试；省略说明符表示发布|

下表中列出的所有库都包含在 \atlmfc\lib 目录中，用于支持的生成体系结构。

|库|说明|
|-------------|-----------------|
|NAFXCW.LIB|MFC 静态链接库，发布版本|
|NAFXCWD.LIB|MFC 静态链接库，调试版本|
|UAFXCW.LIB|具有 Unicode 支持的 MFC 静态链接库，发布版本|
|UAFXCWD.LIB|具有 Unicode 支持的 MFC 静态链接库，调试版本|
|AFXNMCD.LIB|MFC 静态链接库，无 MFC 对话框控件，发布版本|
|AFXNMCDD.LIB|MFC 静态链接库，无 MFC 对话框控件，调试版本|

对于每个静态库，还可以使用具有相同基名称和 .pdb 扩展名的调试器文件。

## <a name="mfc-shared-dll-naming-conventions"></a>MFC 共享 DLL 命名约定

MFC 共享 Dll 还遵循结构化命名约定。 这样，就可以更轻松地了解应该将哪个 DLL 或库用于哪个用途。

MFC Dll 的*版本号*指示二进制文件兼容性。 使用与其他库和编译器工具集具有相同版本的 MFC Dll 来保证项目中的兼容性。

|DLL|描述|
|---------|-----------------|
|MFC*版本*。.DLL|MFC DLL、ANSI 或 MBCS 发行版本|
|MFC*版本*U .dll|MFC DLL，Unicode 版本|
|MFC*版本*d. .dll|MFC DLL、ANSI 或 MBCS 调试版本|
|MFC*版本*UD。.DLL|MFC DLL，Unicode 调试版本|
|MFCM*版本*。.DLL|具有 Windows 窗体控件、ANSI 或 MBCS 发布版本的 MFC DLL|
|MFCM*版本*|带有 Windows 窗体控件的 MFC DLL，Unicode 发行版本|
|MFCM*版本*d. .dll|具有 Windows 窗体控件、ANSI 或 MBCS 调试版本的 MFC DLL|
|MFCM*版本*UD。.DLL|带有 Windows 窗体控件的 MFC DLL，Unicode 调试版本|

生成使用这些共享 Dll 的应用程序或 MFC 扩展 Dll 所需的导入库具有与 DLL 相同的基名称，但具有 .lib 文件扩展名。 使用共享 Dll 时，必须仍将一个小型静态库与代码链接在一起;此库名为 MFCS*版本*{U} {D} .lib。

如果动态链接到 MFC 的共享 DLL 版本，无论该版本是来自应用程序还是来自 MFC 扩展 DLL，都必须包含匹配的 MFC*版本*。DLL 或 MFC*版本*的 .dll。

有关可与应用程序一起分发的 Visual C++ Dll 的列表，请参阅[Microsoft Visual Studio 2017 和 Microsoft Visual Studio 2017 SDK 的可分发代码（包括实用程序和 BuildServer 文件）](/visualstudio/productinfo/2017-redistribution-vs)或[Visual Studio 2019 的可分发代码](/visualstudio/releases/2019/redistribution)。

有关 MFC 中的 MBCS 和 Unicode 支持的详细信息，请参阅[unicode 和多字节字符集（MBCS）支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

## <a name="dynamic-link-library-support"></a>动态链接库支持

可以使用静态或共享动态 MFC 库来创建可供 MFC 和非 MFC 可执行文件使用的 Dll。 它们称为 "规则 Dll" 或 "常规 MFC Dll"，用于将它们与只能由 MFC 应用程序和 MFC Dll 使用的 MFC 扩展 Dll 区分开来。 使用 MFC 静态库生成的 DLL 有时称为 USRDLL，因为 MFC DLL 项目定义预处理器符号** \_ USRDLL**。 使用 MFC 共享 Dll 的 DLL 有时称为 AFXDLL，因为它定义预处理器符号** \_ AFXDLL**。

通过链接到 MFC 静态库来创建 DLL 项目时，可以在不使用 MFC 共享 Dll 的情况下部署 DLL。 当 DLL 项目链接到导入库时，MFC*版本*。LIB 或 MFC*版本*U. 您必须部署匹配的 MFC 共享 DLL MFC*版本*。DLL 或 MFC*版本*U .DLL 和 dll 一起提供。 有关详细信息，请参阅[dll](../build/dlls-in-visual-cpp.md)。

## <a name="see-also"></a>另请参阅

[常规 MFC 主题](general-mfc-topics.md)

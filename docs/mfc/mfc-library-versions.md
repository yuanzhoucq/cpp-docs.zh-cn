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
ms.openlocfilehash: b8e32366d9ff43bd6e5770f64f0ba9d8bf6e56ab
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524786"
---
# <a name="mfc-library-versions"></a>MFC 库版本

MFC 库现已推出了支持 ANSI 单字节和多字节字符集 (MBCS) 代码，以及支持 Unicode （编码为 UTF 16LE，Windows 本机字符集） 的版本。 为静态库或作为共享 DLL，每个 MFC 版本才可用。 还有省略了 MFC 控件的对话框的大小非常敏感，并且不需要这些控件的应用程序的较小的 MFC 静态库版本。 MFC 库是适用于这两个调试和发布版本的支持包括 x86、 x64 和 ARM 处理器的体系结构。 可以创建两个应用程序 （.exe 文件） 和与任何版本的 MFC 库的 Dll。 有一组的 MFC 库编译与托管代码进行连接。 MFC 共享 Dll 包括版本号来指示库二进制兼容性。

## <a name="automatic-linking-of-mfc-library-versions"></a>自动链接 MFC 库版本

MFC 标头文件自动确定正确版本的 MFC 库链接，基于在生成环境中定义的值。 MFC 标头文件添加编译器指令指示链接器以特定版本的 MFC 库中的链接。

例如，AFX。H 标头文件指示链接器链接中的完整静态的有限静态，或共享 DLL 版本的 MFC;ANSI/MBCS 或 Unicode 版本;和调试版本还是发布版本，具体取决于你的生成配置：

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

MFC 标头文件还包含所需的所有库，包括 MFC 库、 Win32 库、 OLE 库、 从示例生成的 OLE 库、 ODBC 库等中链接的指令。

## <a name="ansi-mbcs-and-unicode"></a>ANSI、 MBCS 和 Unicode

支持 MFC ANSI/MBCS 库版本，如 ASCII，这两个单字节字符集和多字节字符设置如 Shift JIS。 MFC Unicode 库版本支持 Unicode UTF 16LE 宽字符编码形式。 对于 utf-8 编码的 Unicode 支持使用 ANSI/MBCS 库版本的 MFC。

若要设置你的项目配置为在 IDE 中使用单字节、 多字节，或宽字符 Unicode 字符串和字符支持，请使用**项目属性**对话框。 在中**配置属性** > **常规**页上，将**字符集**属性设置为**未设置**使用单字节字符集。 将属性设置为**使用多字节字符集**使用多字节字符集，或设置为**使用 Unicode 字符集**使用 Unicode 编码为 utf-16。

MFC 项目使用的预处理器符号\_UNICODE 以指示 utf-16 的宽字符 Unicode 支持和\_MBCS，若要指示 MBCS 支持。 这些选项是互斥的项目中。

## <a name="mfc-static-library-naming-conventions"></a>MFC 静态库命名约定

Mfc 静态库使用以下命名约定。 库名采用以下格式

> <em>u</em>AFX<em>cd</em>.LIB

其中，使用斜体小写字母形式显示的字母是说明符的占位符，下表中显示了说明符的含义：

|说明符|值和含义|
|---------------|-------------------------|
|*u*|ANSI/MBCS (N) 或 Unicode (U);对于不带 MFC 控件在对话框中的版本可以省略参数|
|*c*|使用 MFC 控件在对话框 (CW) 或不 (NMCD) 版本|
|*d*|调试或发布：D = 调试;省略说明符表示发布|

下表中列出的所有库都都包含预构建支持的生成体系结构的 \atlmfc\lib 目录中。

|库|描述|
|-------------|-----------------|
|NAFXCW.LIB|MFC 静态链接库，发布版本|
|NAFXCWD.LIB|MFC 静态链接库，调试版本|
|UAFXCW.LIB|具有 Unicode 支持的 MFC 静态链接库，发布版本|
|UAFXCWD.LIB|具有 Unicode 支持的 MFC 静态链接库，调试版本|
|AFXNMCD.LIB|不带 MFC 对话框控件，发行版的 MFC 静态链接库|
|AFXNMCDD.LIB|不带 MFC 对话框控件，调试版本的 MFC 静态链接库|

具有相同的基名称和扩展名为.pdb 的调试器文件也已可供每个静态库。

## <a name="mfc-shared-dll-naming-conventions"></a>共享 MFC DLL 命名约定

MFC 共享 Dll 还遵循结构化的命名约定。 这使得更方便地了解哪个 DLL 或库，则应当使用用于哪些目的。

MFC Dll 已*版本*指示二进制文件兼容性的数字。 使用 MFC Dll 具有与其他库和编译器工具集，以保证兼容性项目中的相同的版本。

|DLL|描述|
|---------|-----------------|
|MFC*version*.DLL|MFC DLL、 ANSI 或 MBCS 版本的版本|
|MFC*version*U.DLL|MFC DLL，Unicode 版本|
|MFC*version*D.DLL|MFC DLL、 ANSI 或 MBCS 调试版本|
|MFC*version*UD.DLL|MFC DLL，Unicode 调试版本|
|MFCM*version*.DLL|与 Windows 窗体控件，MFC DLL ANSI 或 MBCS 版本的版本|
|MFCM*version*U.DLL|与 Windows 窗体控件，Unicode 版本的 MFC DLL|
|MFCM*version*D.DLL|与 Windows 窗体控件，MFC DLL ANSI 或 MBCS 调试版本|
|MFCM*version*UD.DLL|与 Windows 窗体控件，Unicode 调试版本的 MFC DLL|

生成应用程序或 MFC 扩展 Dll 使用这些共享的 Dll 所需的导入库具有相同的基名称与 DLL，但扩展名为.lib 文件名称。 当你使用共享的 Dll 时，在小型静态库，仍必须与你的代码; 链接此库名为 MFCS*版本*{U} {D}.lib。

如果您要动态链接到共享的 DLL 版本的 MFC，，是否从应用程序或从 MFC 扩展 DLL，则必须包含匹配的 MFC*版本*。DLL 或 MFC*版本*U.DLL 时部署您的产品。

有关视觉对象的列表C++Dll 可以随您的应用程序分发，请参阅[Microsoft Visual Studio 2017 和 Microsoft Visual Studio 2017 SDK （包括实用程序和 BuildServer 文件） 的可分发代码](/visualstudio/productinfo/2017-redistribution-vs)或[可分发代码 Visual Studio 2019](/visualstudio/releases/2019/redistribution)。

MFC 中的 MBCS 和 Unicode 支持的详细信息，请参阅[Unicode 和多字节字符集 (MBCS) 支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

## <a name="dynamic-link-library-support"></a>动态链接库支持

静态或共享动态 MFC 库可用于创建可由 MFC 和非 MFC 可执行文件的 Dll。 这些测试称为"的规则 Dll"规则 MFC Dll"，以区别于 MFC 扩展 Dll 只能是由 MFC 应用程序和 MFC Dll。 使用 MFC 静态库生成的 DLL 有时称为 USRDLL 在较旧的引用，因为 MFC DLL 项目定义预处理器符号 **\_USRDLL**。 使用 MFC 共享 Dll 的 DLL 有时称为 AFXDLL 在较旧的引用，因为它定义预处理器符号 **\_AFXDLL**。

通过链接到 MFC 静态库创建 DLL 项目，不需要 MFC 共享 Dll 可以部署您的 DLL。 DLL 项目时链接到 MFC 的导入库*版本*。LIB 或 MFC*版本*U.LIB，必须部署的匹配 MFC 共享 DLL MFC*版本*。DLL 或 MFC*版本*U.DLL 以及您的 DLL。 有关详细信息，请参阅[Dll](../build/dlls-in-visual-cpp.md)。

## <a name="see-also"></a>请参阅

[常规 MFC 主题](../mfc/general-mfc-topics.md)

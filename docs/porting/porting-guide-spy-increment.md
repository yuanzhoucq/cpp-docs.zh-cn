---
title: 移植指南：Spy++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e558f759-3017-48a7-95a9-b5b779d5e51d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd85aa6ce1cfee3416d04291d484a7bad6359ea4
ms.sourcegitcommit: 072e12d6b7a242765bdcc9afe4a14a284ade01fc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/26/2018
ms.locfileid: "50136180"
---
# <a name="porting-guide-spy"></a>迁移指南：Spy++

此移植案例研究旨在让你了解典型的移植项目、可能遇到的问题类型，以及解决移植问题的一些常用提示和技巧。 这并不是权威的移植指南，因为移植项目的体验很大程度取决于代码的详细信息。

## <a name="spy"></a>Spy++

Spy++ 是广泛使用的 GUI 诊断工具，适用于提供有关 Windows 桌面上用户界面元素的各种类型信息的 Windows 桌面。 它显示了 Windows 的完整层次结构，并提供有关每个窗口和控件的元数据的访问。 多年来，这款有用的应用程序均与 Visual Studio 一起提供。 我们找到了上次在 Visual C++ 6.0 中编译的旧版本应用程序，并将其移植到了 Visual Studio 2015。 对于 Visual Studio 2017 来说，步骤几乎完全相同。

我们认为这是最典型的移植使用 MFC 和 Win32 API 的 Windows 桌面应用程序的情况，尤其是对于尚未使用从 Visual C++ 6.0 版本开始的任意 Visual C++ 版本进行更新的旧项目。

##  <a name="convert_project_file"></a>步骤 1. 转换项目文件。

项目文件（Visual C++ 6.0 中两个旧的 .dsw 文件）轻松转换，且未产生任何需要进一步关注的问题。 其中一个项目是 Spy++ 应用程序。 另一个项目是 SpyHk，它是用 C 语言编写的支持 DLL。 如[此处](../porting/visual-cpp-porting-and-upgrading-guide.md)所述，更复杂的项目可能无法轻松升级。

升级两个项目后，我们的解决方案如下所示：

![Spy ++ 解决方案](../porting/media/spyxxsolution.PNG "SpyxxSolution")

我们共有两个项目，一个具有大量的 C++ 文件，另一个是用 C 语言编写的 DLL。

##  <a name="header_file_problems"></a>步骤 2. 头文件问题

生成新转换的项目后，通常首先发现的是，找不到自己项目使用的头文件。

Spy++ 中无法找到的文件是 verstamp.h。 通过搜索 Internet，我们确定这是因为 DAO SDK（一种过时的数据技术）。 我们想知道使用了该头文件中的哪些符号，以确定是否真的需要该文件或者是否在其他地方定义了这些符号，因此我们注释了掉头文件声明并重新进行了编译。 事实证明只需要一个符号，即 VER_FILEFLAGSMASK。

```Output
1>C:\Program Files (x86)\Windows Kits\8.1\Include\shared\common.ver(212): error RC2104: undefined keyword or key name: VER_FILEFLAGSMASK
```

在可用的包含文件中查找符号最简单的方法是，使用“在文件中查找”(Ctrl+Shift+F)，并指定“Visual C++ 包含目录”。 我们在 ntverp.h 中找到了该符号。 我们将 verstamp.h 包含文件替换为 ntverp.h 后，此错误消失。

##  <a name="linker_output_settings"></a>步骤 3. 链接器 OutputFile 设置

有时，旧项目将文件放在非常规位置，升级后这可能会导致问题。 在这种情况下，我们必须将 `$(SolutionDir)` 添加到项目属性的包含路径，以确保 Visual Studio 可以找到放在此处而非放在某个项目文件夹中的头文件。

MSBuild 发出 MSB8012，报告 Link.OutputFile 属性与 TargetPath 和 TargetName 值不匹配。

```Output
warning MSB8012: TargetPath(...\spyxx\spyxxhk\.\..\Debug\SpyxxHk.dll) does not match the Linker's OutputFile property value (...\spyxx\Debug\SpyHk55.dll). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).warning MSB8012: TargetName(SpyxxHk) does not match the Linker's OutputFile property value (SpyHk55). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).
```

Link.OutputFile 是生成输出（例如 EXE、DLL），通常由 `$(TargetDir)$(TargetName)$(TargetExt)`（提供路径、文件名和扩展名）构造。 这是一种常见错误，发生在将项目从旧的 Visual C++ 生成工具 (vcbuild.exe) 迁移到新的生成工具 (MSBuild.exe) 时。 由于 Visual Studio 2010 中的生成工具发生变化，因此每当你将 2010 之前的项目迁移到 2010 或更高版本时，就可能会遇到此问题。 基本问题是，项目迁移向导不会更新 **Link.OutputFile** 值，因为并不总是可以根据其他项目设置来确定其值。 因此，通常必须进行手动设置。 有关详细信息，请参阅 Visual C++ 博客上的这篇[文章](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx)。

在这种情况下，对于 Spy++ 项目，转换后的项目中的 **Link.OutputFile** 属性将设置为 .\Debug\Spyxx.exe 或 .\Release\Spyxx.exe，具体取决于配置。 最好的方法就是，针对所有配置将这些硬编码值替换为 `$(TargetDir)$(TargetName)$(TargetExt)`。 如果不起作用，则可以从此处自定义，或更改设置这些值的“常规”部分中的属性（属性为“输出目录”、“目标文件名”和“目标文件扩展名”）。 记住，如果正在查看的属性使用宏，则可以选择下拉列表中的“编辑”打开一个对话框，该对话框显示最终的字符串和已进行的宏替换。 你可以通过选择“宏”按钮查看所有可用宏及其当前值。

##  <a name="updating_winver"></a>步骤 4. 更新目标 Windows 版本

下一个错误指示 WINVER 版本不再受 MFC 支持。 适用于 Windows XP 的 WINVER 是 0x0501。

```Output
C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxv_w32.h(40): fatal error C1189: #error:  MFC does not support WINVER less than 0x0501.  Please change the definition of WINVER in your project properties or precompiled header.
```

Microsoft 不再为 Windows XP 提供支持，因此，即使 Visual Studio 中允许面向 Windows XP，你仍应在应用程序中逐步取消对此版本的支持，并鼓励你的用户采用新版本的 Windows。

若要消除此错误，请将“项目属性”设置更新为当前要面向的最低版本的 Windows，以定义 WINVER。 [此处](/windows/desktop/WinProg/using-the-windows-headers)可找到包含各种 Windows 版本的值的表。

Stdafx.h 文件包含一些宏定义。

```cpp
#define WINVER       0x0500  // these defines are set so that we get the
#define _WIN32_WINNT 0x0500  // maximum set of message/flag definitions,
#define _WIN32_IE    0x0400  // from both winuser.h and commctrl.h.
```

将设置为 Windows 7 的 WINVER。 如果将宏而不是值本身 (0x0601) 用于 Windows 7 (_WIN32_WINNT_WIN7)，之后读取代码将会更容易。

```cpp
#define WINVER _WINNT_WIN32_WIN7 // Minimum targeted Windows version is Windows 7
```

##  <a name="linker_errors"></a>步骤 5. 链接器错误

进行这些更改后，可以生成 SpyHk (DLL) 项目，但会产生链接器错误。

```Output
LINK : warning LNK4216: Exported entry point _DLLEntryPoint@12
```

不应导出 DLL 的入口点。 入口点仅用于在 DLL 首次加载到内存中时，由加载程序进行调用，因此它不应该在其他调用方所在的导出表中。 我们只需确保未向入口点附加 __declspec(dllexport) 指令。 在 spyxxhk.cz 中，我们必须从 `DLLEntryPoint` 的声明和定义这两个地方删除入口点。 使用此指令没有任何意义，但以前版本的链接器和编译器并未将其标记为问题。 而较新版本的链接器会发出警告。

```cpp
// deleted __declspec(dllexport)
BOOL WINAPI DLLEntryPoint(HINSTANCE hinstDLL,DWORD fdwReason, LPVOID lpvReserved);
```

现在，可以生成 C DLL 项目 SpyHK.dll，而且链接不会出错。

##  <a name="outdated_header_files"></a>步骤 6. 更多过时的头文件

从这一步骤开始，我们将对主要的可执行项目 Spyxx 执行操作。

找不到其他几个包含文件：ctl3d.h 和 penwin.h。 虽然通过搜索 Internet 尝试识别包含标头的内容可能有用，但有时信息作用并不大。 我们发现 ctl3d.h 是 Exchange 开发工具包的一部分，并且对 Windows 95 上的某些控件样式以及与 Window Pen Computin（一个过时的 API）相关的 penwin.h 提供支持。 在这种情况下，我们只需注释掉 `#include` 行，并用处理 verstamp.h 的方式处理未定义的符号。 与 3D 控件或 Pen Computing 相关的所有内容均已从项目中删除。

如果项目中包含许多要逐渐消除的编译错误，则删除 `#include` 指令时立即找到所有使用过时 API 的情况并不现实。 我们没有立即检测到它，却在稍后出现一个未定义 WM_DLGBORDER 的错误。 它实际上是来自 ctl3d.h 的许多未定义符号之一。 一旦确定它与过时的 API 相关后，则可以在代码中删除对它所有的引用。

##  <a name="updating_iostreams_code"></a>步骤 7. 更新旧的 iostreams 代码

下一个错误是使用 iostreams 的旧 C++ 代码的常见错误。

```Output
mstream.h(40): fatal error C1083: Cannot open include file: 'iostream.h': No such file or directory
```

问题在于已删除并已替换旧的 iostreams 库。 我们必须将旧的 iostreams 替换为较新的标准。

```cpp
#include <iostream.h>
#include <strstrea.h>
#include <iomanip.h>
```

这些是更新的包含项：

```cpp
#include <iostream>
#include <sstream>
#include <iomanip>
```

进行此更改后，`ostrstream` 出现问题，因此不再使用。 适当的替换为 ostringstream。 我们尝试添加 `ostrstream` 的 typedef，以避免修改太多代码（至少作为一个开始）。

```cpp
typedef std::basic_ostringstream<TCHAR> ostrstream;
```

当前，项目正使用 MBCS（多字节字符集）进行生成，因此 char 是合适的字符数据类型。 但是，为了实现更轻松地将代码更新为 UTF-16 Unicode，我们将其更新为 `TCHAR`，TCHAR 解析为 char 或 wchar_t，具体取决于项目设置中的“字符集”属性是否设置为 MBCS 或 Unicode。

其他一些代码需要进行更新。  我们将基类 `ios` 替换为了 `ios_base`，并将 ostream is 替换为了 basic_ostream\<T>。 我们添加了两个额外的 typedef，并编译此部分。

```cpp
typedef std::basic_ostream<TCHAR> ostream;
typedef ios_base ios;
```

使用这些 typedef 只是一种临时解决方案。 为了实现更永久的解决方案，可以更新对重命名或过时 API 的每个引用。

以下是下一个错误。

```Output
error C2039: 'freeze': is not a member of 'std::basic_stringbuf<char,std::char_traits<char>,std::allocator<char>>'
```

下一个问题在于 `basic_stringbuf` 没有 `freeze` 方法。 `freeze` 方法用于防止旧 `ostream` 发生内存泄漏。 现在使用了新的 `ostringstream`，就不再需要此方法。 我们可以删除对 `freeze` 的调用。

```cpp
//rdbuf()->freeze(0);
```

接下来的两个错误发生在相邻的行上。 第一个错误报告使用 `ends`，这是旧 `iostream` 库中将 null 终止符添加到字符串的 IO 操控程序。 第二个错误说明 `str` 方法的输出不能分配给非常量指针。

```cpp
// Null terminate the string in the buffer and
// get a pointer to it.
//
*this << ends;
LPSTR psz = str();
```

```Output
2>mstream.cpp(167): error C2065: 'ends': undeclared identifier2>mstream.cpp(168): error C2440: 'initializing': cannot convert from 'std::basic_string<char,std::char_traits<char>,std::allocator<char>>' to 'LPSTR'
```

使用新的流库时，由于字符串始终不以 null 结尾，因此无需 `ends`，以便删除该行。 第二个问题在于现在 `str()` 不返回指向字符串字符数组的指针，而是返回 `std::string` 类型。 第二个问题的解决方案是，将类型更改为 `LPCSTR` 并使用 `c_str()` 方法请求指针。

```cpp
//*this << ends;
LPCTSTR psz = str().c_str();
```

此代码上曾出现过令人困扰的错误。

```cpp
MOUT << _T(" chUser:'") << chUser
<< _T("' (") << (INT)(UCHAR)chUser << _T(')');
```

宏 MOUT 解析为 `*g_pmout`，这是类型为 `mstream` 的对象。 `mstream` 类派生自标准输出字符串类 `std::basic_ostream<TCHAR>`。 但字符串文本周围有 \_T，我们放置此宏的目的在于为转换到 Unicode 做准备，运算符 << 的重载解决方案失败，并出现以下错误消息：

```Output
1>winmsgs.cpp(4612): error C2666: 'mstream::operator <<': 2 overloads have similar conversions
1>  c:\source\spyxx\spyxx\mstream.h(120): note: could be 'mstream &mstream::operator <<(ios &(__cdecl *)(ios &))'
1>  c:\source\spyxx\spyxx\mstream.h(118): note: or       'mstream &mstream::operator <<(ostream &(__cdecl *)(ostream &))'
1>  c:\source\spyxx\spyxx\mstream.h(116): note: or       'mstream &mstream::operator <<(ostrstream &(__cdecl *)(ostrstream &))'
1>  c:\source\spyxx\spyxx\mstream.h(114): note: or       'mstream &mstream::operator <<(mstream &(__cdecl *)(mstream &))'
1>  c:\source\spyxx\spyxx\mstream.h(109): note: or       'mstream &mstream::operator <<(LPTSTR)'
1>  c:\source\spyxx\spyxx\mstream.h(104): note: or       'mstream &mstream::operator <<(TCHAR)'
1>  c:\source\spyxx\spyxx\mstream.h(102): note: or       'mstream &mstream::operator <<(DWORD)'
1>  c:\source\spyxx\spyxx\mstream.h(101): note: or       'mstream &mstream::operator <<(WORD)'
1>  c:\source\spyxx\spyxx\mstream.h(100): note: or       'mstream &mstream::operator <<(BYTE)'
1>  c:\source\spyxx\spyxx\mstream.h(95): note: or       'mstream &mstream::operator <<(long)'
1>  c:\source\spyxx\spyxx\mstream.h(90): note: or       'mstream &mstream::operator <<(unsigned int)'
1>  c:\source\spyxx\spyxx\mstream.h(85): note: or       'mstream &mstream::operator <<(int)'
1>  c:\source\spyxx\spyxx\mstream.h(83): note: or       'mstream &mstream::operator <<(HWND)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1132): note: or       'CDumpContext &operator <<(CDumpContext &,COleSafeArray &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1044): note: or       'CArchive &operator <<(CArchive &,ATL::COleDateTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1042): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::COleDateTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1037): note: or       'CArchive &operator <<(CArchive &,ATL::COleDateTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1035): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::COleDateTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1030): note: or       'CArchive &operator <<(CArchive &,COleCurrency)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1028): note: or       'CDumpContext &operator <<(CDumpContext &,COleCurrency)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(955): note: or       'CArchive &operator <<(CArchive &,ATL::CComBSTR)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(951): note: or       'CArchive &operator <<(CArchive &,COleVariant)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(949): note: or       'CDumpContext &operator <<(CDumpContext &,COleVariant)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(248): note: or       'CArchive &operator <<(CArchive &,const RECT &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(247): note: or       'CArchive &operator <<(CArchive &,POINT)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(246): note: or       'CArchive &operator <<(CArchive &,SIZE)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(242): note: or       'CDumpContext &operator <<(CDumpContext &,const RECT &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(241): note: or       'CDumpContext &operator <<(CDumpContext &,POINT)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(240): note: or       'CDumpContext &operator <<(CDumpContext &,SIZE)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1639): note: or       'CArchive &operator <<(CArchive &,const CObject *)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1425): note: or       'CArchive &operator <<(CArchive &,ATL::CTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1423): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::CTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1418): note: or       'CArchive &operator <<(CArchive &,ATL::CTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1416): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::CTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(694): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const char *)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(741): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(866): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const _Elem *)'
1>          with
1>          [
1>              _Elem=wchar_t
1>          ]
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(983): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>,wchar_t[10]>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &&,const _Ty (&))'
1>          with
1>          [
1>              _Ty=wchar_t [10]
1>          ]
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(1021): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const std::error_code &)'
1>  winmsgs.cpp(4612): note: while trying to match the argument list '(CMsgStream, const wchar_t [10])'
```

存在很多运算符 << 定义，使这种错误看起来很严重。 详细查看可用的重载后，可以看到多数都是不相关的，而进一步仔细查看 `mstream` 类定义后，我们发现了下面的函数，我们认为在这种情况下应调用该函数。

```cpp
mstream& operator<<(LPTSTR psz)
{
  return (mstream&)ostrstream::operator<<(psz);
}
```

不调用它的原因是，字符串文本具有 `const wchar_t[10]` 类型（正如你可以从长错误消息的最后一行所看到），因此不会自动转换为非常量指针。 但是，该运算符不应修改输入参数，因此更合适的参数类型是 `LPCTSTR`（作为 MBCS 编译时是 `const char*`，作为 Unicode 编译时是 `const wchar_t*`），而不是 `LPTSTR`（作为 MBCS 编译时是 `char*`，作为 Unicode 编译时是 `wchar_t*`）。 进行此更改可修复该错误。

旧的、不太严格的编译器允许这种类型的转换，但最新的符合性更改则要求更正确的代码。

##  <a name="stricter_conversions"></a> 步骤 8. 编译器的更严格转换

我们还获得了如下所示的许多错误：

```Output
error C2440: 'static_cast': cannot convert from 'UINT (__thiscall CHotLinkCtrl::* )(CPoint)' to 'LRESULT (__thiscall CWnd::* )(CPoint)'
```

该错误发生在只是宏的消息映射中：

```cpp
BEGIN_MESSAGE_MAP(CFindToolIcon, CWnd)
// other messages omitted...
ON_WM_NCHITTEST() // Error occurs on this line.
END_MESSAGE_MAP()
```

转到此宏的定义，可以看到它引用了函数 `OnNcHitTest`。

```cpp
#define ON_WM_NCHITTEST() \
{ WM_NCHITTEST, 0, 0, 0, AfxSig_l_p, \
(AFX_PMSG)(AFX_PMSGW) \
(static_cast< LRESULT (AFX_MSG_CALL CWnd::*)(CPoint) > (&ThisClass :: OnNcHitTest)) },
```

此问题与指向成员函数类型的指针中的不匹配相关。 问题不在于从 `CHotLinkCtrl`（作为类类型）转换为 `CWnd`（作为类类型），因为这是有效的派生类到基类转换。 问题是返回类型：UINT 与 LRESULT。 LRESULT 将解析为 LONG_PTR（即 64 位指针或 32 位指针，具体取决于目标二进制类型），因此 UINT 不转换为此类型。 由于在 Visual Studio 2005 中，作为 64 位兼容性更改的一部分，许多消息映射方法的返回类型已从 UINT 更改为 LRESULT，这在升级在 2005 年之前编写的代码时并不罕见。 我们将以下代码的返回类型从 UINT 更改为 LRESULT：

```cpp
afx_msg UINT OnNcHitTest(CPoint point);
```

更改后，将得到以下代码：

```cpp
afx_msg LRESULT OnNcHitTest(CPoint point);
```

由于从 CWnd 派生的不同类中总共出现了此函数的大约十个匹配项，当光标位于编辑器的函数上时，使用“转到定义”（键盘：F12）和“转到声明”（键盘：Ctrl+F12）有助于从“查找符号”工具窗口定位并导航到这些函数。 “转到定义”通常是两个选项中更有用的。 “转到声明”将查找声明而不是定义类声明，例如友元类声明或前向引用。

##  <a name="mfc_changes"></a>步骤 9. MFC 更改

下一个错误也与更改的声明类型有关，并且还会发生在宏中。

```Output
error C2440: 'static_cast': cannot convert from 'void (__thiscall CFindWindowDlg::* )(BOOL,HTASK)' to 'void (__thiscall CWnd::* )(BOOL,DWORD)'
```

问题在于 `CWnd::OnActivateApp` 的第二个参数从 HTASK 更改为了 DWORD。 此更改发生在 2002 年版的 Visual Studio、Visual Studio .NET 中。

```cpp
afx_msg void OnActivateApp(BOOL bActive, HTASK hTask);
```

我们必须相应更新派生类中的 OnActivateApp 的声明，如下所示：

```cpp
afx_msg void OnActivateApp(BOOL bActive, DWORD dwThreadId);
```

在此步骤中，我们将能够编译项目。 有几个警告需要解决，但是可以选择部分进行升级，例如从 MBCS 转换为 Unicode 或通过使用安全 CRT 函数提高安全性。

##  <a name="compiler_warnings"></a>步骤 10. 解决编译器警告

若要获取完整的警告列表，则应对解决方案执行“全部重新生成”而不是普通生成，从而确保以前编译的所有内容均将重新编译，因为你只能从当前的编译获取警告报表。 另一个问题在于是接受当前警告级别还是使用更高的警告级别。  移植大量代码（尤其是旧代码）时，使用更高的警告级别更恰当。  你可能还想从默认警告级别开始，然后增加警告级别以获取所有警告。 如果使用 `/Wall`，则可以获得系统头文件中的一些警告，多数人都使用 `/W4` 来获取有关其代码的大部分警告，而不获取系统头文件的警告。 如果希望警告显示为错误，则需添加 `/WX` 选项。 这些设置在“项目属性”对话框的 C/C++ 部分中。

`CSpyApp` 类中的方法之一将产生有关不再受支持的函数的警告。

```cpp
void SetDialogBkColor() {CWinApp::SetDialogBkColor(::GetSysColor(COLOR_BTNFACE));}
```

警告如下所示。

```Output
warning C4996: 'CWinApp::SetDialogBkColor': CWinApp::SetDialogBkColor is no longer supported. Instead, handle WM_CTLCOLORDLG in your dialog
```

WM_CTLCOLORDLG 消息已在 Spy++ 代码中进行了处理，因此需要的唯一更改是删除对 `SetDialogBkColor` 的不再需要的所有引用。

下一个警告的修复非常简单，注释掉变量名称即可。 我们收到了以下警告：

```Output
warning C4456: declaration of 'lpszBuffer' hides previous local declaration
```

生成此警告的代码涉及宏。

```cpp
DECODEPARM(CB_GETLBTEXT)
{
  P2WPOUT();

  P2LPOUTPTRSTR;
  P2IFDATA()
  {
    PARM(lpszBuffer, PPACK_STRINGORD, ED2);

    INDENT();

    P2IFISORD(lpszBuffer)
    {
      P2OUTORD(lpszBuffer);
    }
    else
    {
      PARM(lpszBuffer, LPTSTR, ED2);
      P2OUTS(lpszBuffer);
    }
  }
}
```

此代码中使用大量的宏导致代码哪一维护。 在本例中，宏包括变量的声明。 宏 PARM 的定义如下：

```cpp
#define PARM(var, type, src)type var = (type)src
```

因此，`lpszBuffer` 变量在相同的函数中进行了两次声明。 如果代码未使用宏（只需删除第二个类型声明），则修复这个问题并不容易。 事实上，我们面对的选择很艰难，必须决定是将宏代码重写为普通代码（单调乏味并且可能出错的任务）还是禁用该警告。

在本例中，我们选择禁用该警告。 可以通过添加如下杂注实现此操作：

```cpp
#pragma warning(disable : 4456)
```

禁用警告时，你可能需要将禁用限制为只对产生警告的代码起作用，以避免在可能提供有用信息时禁止显示警告。 我们在产生警告的行之后添加代码以还原警告，或者因为宏中发生警告，最好使用在宏中起作用的 __pragma 关键字（`#pragma` 在宏中不起作用）。

```cpp
#define PARM(var, type, src)__pragma(warning(disable : 4456))  \
type var = (type)src \
__pragma(warning(default : 4456))
```

下一个警告需要进行一些代码修订。 已弃用 Win32 API `GetVersion` 和 `GetVersionEx`。

```Output
warning C4996: 'GetVersion': was declared deprecated
```

下面的代码演示如何获取版本。

```cpp
// check Windows version and set m_bIsWindows9x/m_bIsWindows4x/m_bIsWindows5x flags accordingly.
DWORD dwWindowsVersion = GetVersion();
```

后面紧跟检查 dwWindowsVersion 值以确定是否在 Windows 95 上运行以及确定 Windows NT 版本的大量代码。 由于这已过时，我们将删除代码并处理对这些变量的所有引用。

文章 [Operating system version changes in Windows 8.1 and Windows Server 2012 R2](https://msdn.microsoft.com/library/windows/desktop/dn302074.aspx)（Windows 8.1 和 Windows Server 2012 R2中的操作系统版本更改）解释了这一情况。

`CSpyApp` 类中有一些查询操作系统版本的方法：`IsWindows9x`、`IsWindows4x` 和 `IsWindows5x`。 对于旧应用程序使用的技术而言，良好的开端在于假定我们计划支持的 Windows 版本（Windows 7 和更高版本）都非常接近 Windows NT 5。 这些方法用于应对旧操作系统的限制。 因此，我们更改了这些方法，以对 `IsWindows5x` 返回 TRUE，对其他返回 FALSE。

```cpp
BOOL IsWindows9x() {/*return(m_bIsWindows9x);*/ return FALSE;  }
BOOL IsWindows4x() {/*return(m_bIsWindows4x);*/ return FALSE;  }
BOOL IsWindows5x() {/*return(m_bIsWindows5x);*/ return TRUE;  }
```

只剩下少数几个直接使用内部变量的地方。 由于删除了这些变量，我们将获得几个必须显式处理的错误。

```Output
error C2065: 'm_bIsWindows9x': undeclared identifier
```

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(m_bIsWindows9x || hToolhelp32 != NULL);
}
```

可以将其替换为方法调用，或者仅传递 TRUE 并删除 Windows 9x 中的旧特殊用例。

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(TRUE /*!m_bIsWindows9x || hToolhelp32 != NULL*/);
}
```

默认级别 (3) 的最终警告与位域相关。

```Output
treectl.cpp(1656): warning C4463: overflow; assigning 1 to bit-field that can only hold values from -1 to 0
```

触发此错误的代码如下所示。

```cpp
m_bStdMouse = TRUE;
```

`m_bStdMouse` 的声明指示它是位域。

```cpp
class CTreeListBox : public CListBox
{
  DECLARE_DYNCREATE(CTreeListBox)

  CTreeListBox();

  private:
  int ItemFromPoint(const CPoint& point);

  class CTreeCtl* m_pTree;
  BOOL m_bGotMouseDown : 1;
  BOOL m_bDeferedDeselection : 1;
  BOOL m_bStdMouse : 1;
```

此代码在 Visual C++ 支持内置的 bool 类型前编写。 在此类代码中，BOOL 是 int 的 typedef。int 类型是带符号类型，而带符号 int 的位表示是将第一个位用作符号位，以便 int 类型的位域可以解释为表示 0 或 -1，结果可能超出预期。

通过查看代码无法知道这些为什么是位域。 是否打算保持较小的对象尺寸？或者是否有任何地方使用该对象的二进制布局？ 由于没有使用位域的原因，我们将它们更改为了普通 BOOL 成员。 使用位域来使对象保持小尺寸并不能保证有效。 这取决于编译器如何布局类型。

你可能想知道使用整个标准类型 bool 是否有用。 很多旧代码模式（如 BOOL 类型）都可用于解决之后在标准 C++ 中解决的问题，因此从 BOOL 更改为 bool 内置类型只是此类更改的其中一个示例，当你获取最初在新版本中运行的代码后，通常会考虑此更改。

处理完默认级别（等级 3）出现的所有警告后，更改为级别 4，以捕获其他警告。 首先出现如下警告：

```Output
warning C4100: 'nTab': unreferenced formal parameter
```

产生此警告的代码如下所示。

```cpp
virtual void OnSelectTab(int nTab) {};
```

这看起来无害，但由于我们希望使用 `/W4` 和 `/WX` 集进行干净的编译，因此只需注释掉变量名，保留是为了提高可读性。

```cpp
virtual void OnSelectTab(int /*nTab*/) {};
```

我们收到的其他警告有助于进行常规的代码清理。 从 int 或 unsigned int 到 WORD（即 unsigned short 的 typedef）存在许多隐式转换。 这可能会导致数据丢失。 在这些情况下，我们添加了到 WORD 的强制转换。

以下是我们获得的关于此代码的另一个级别 4 警告：

```Output
warning C4211: nonstandard extension used: redefined extern to static
```

该问题发生在变量首先声明 extern 再声明 static 时。 这两个存储类说明符的含义是互斥的，但作为 Microsoft 扩展这是允许的。 如果希望代码可移植到其他编译器，或者希望使用 `/Za`（ANSI 兼容性）来编译代码，则可以更改声明以获得匹配的存储类说明符。

##  <a name="porting_to_unicode"></a>步骤 11. 从 MBCS 移植到 Unicode

注意，在 Windows 世界中，当说到 Unicode 时，通常是指 UTF-16。 其他操作系统（如 Linux）使用 UTF-8，但 Windows 通常不使用。 Visual Studio 2013 和 Visual Studio 2015 中弃用了 MFC 的 MBCS 版本，但是 Visual Studio 2017 将不再弃用它。 如果使用的是 Visual Studio 2013 或 Visual Studio 2015，在执行实际将 MBCS 代码移植到 UTF-16 Unicode 的步骤之前，我们可能需要暂时消除已弃用 MBCS 的警告，以便执行其他工作或将移植推迟到方便的时间。 当前的代码使用 MBCS，若要继续使用，则需要安装 ANSI/MBCS 版本的 MFC。 Visual Studio 使用 C++ 的桌面开发的默认安装内容并不包括较大的 MFC 库，因此需要在安装程序的可选组件中将其选中。 请参阅 [MFC MBCS DLL 加载项](../mfc/mfc-mbcs-dll-add-on.md)。 完成下载并重启 Visual Studio 后，可以使用 MBCS 版本的 MFC 进行编译和链接，但若要在使用 Visual Studio 2013 和 Visual Studio 2015 时完全删除关于 MBCS 的警告，则还应将 NO_WARN_MBCS_MFC_DEPRECATION 添加到项目属性预处理器部分的预定义宏列表，或者添加到 stdafx.h 头文件或其他常见头文件的开头。

现在我们将获得一些链接器错误。

```Output
fatal error LNK1181: cannot open input file 'mfc42d.lib'
```

出现 LNK1181 错误的原因是链接器输入中包含 mfc 的过时静态库版本。 不再需要静态库，由于我们可以动态链接 MFC，因此只需从项目属性链接器部分的输入属性中删除所有 MFC 静态库即可。 此项目还使用 `/NODEFAULTLIB` 选项，并改为列出所有库依赖项。

```
msvcrtd.lib;msvcirtd.lib;kernel32.lib;user32.lib;gdi32.lib;advapi32.lib;Debug\SpyHk55.lib;%(AdditionalDependencies)
```

现在让我们实际将旧的多字节字符集 (MBCS) 代码更新为 Unicode。 由于这是一个 Windows 应用程序，它与 Windows 桌面平台联系紧密，因此我们将该应用程序移植到 Windows 使用的 UTF-16 Unicode。 如果你正编写跨平台代码或正将 Windows 应用程序移植到另一个平台，则可能需要考虑移植到其他操作系统广泛使用的 UTF-8。

移植到 UTF-16 Unicode 时，必须决定是否仍然需要编译为 MBCS 的选项。  如果需要具有支持 MBCS 的选项，则应将 TCHAR 宏用作字符类型，它将解析为 char 或 wchar_t，具体取决于是否在编译期间定义了 \_MBCS 或 \_UNICODE。 切换到 TCHAR 及 TCHAR 版本的各种 API 而不是 wchar_t 及其关联 API 意味着你能够重回 MBCS 版本的代码，只需定义 \_MBCS 宏而不是 \_UNICODE 即可。 除 TCHAR 外，还存在各种 TCHAR 版本，如广泛使用的 typedef、宏和函数。 例如，LPCTSTR 而非 LPCSTR，等等。 在项目属性对话框中，在“配置属性”的“常规”部分，将“字符集”属性从“使用 MBCS 字符集”更改为“使用 Unicode 字符集”。 此设置会影响编译期间预定义的宏。 同时存在 UNICODE 宏和 \_UNICODE 宏。 项目属性对两者的影响一致。 Windows 头文件使用 UNICODE，而 Visual C++ 头文件（如 MFC）则使用 \_UNICODE，但定义其中一个后，另一个也将得到定义。

有一个使用 TCHAR 从 MBCS 移植到 UTF-16 Unicode 的好[方法](https://msdn.microsoft.com/library/cc194801.aspx)。 选择此路由。 首先，将“字符集”属性设置为“使用 Unicode 字符集”并重新生成项目。

代码中的一些地方已经使用 TCHAR，显然预期最终支持 Unicode。 有些不使用。 我们搜索 CHAR 的实例，即 char 的 typedef，并将大多数实例替换为了 TCHAR。 此外，我们还搜索了 `sizeof(CHAR)`。 每当从 CHAR 更改为 TCHAR 时，通常不得不更改为 `sizeof(TCHAR)`，因为这通常用于确定字符串中的字符数。 此处使用错误的类型不会产生编译器错误，因此需要注意此情况。

切换到 Unicode 后，这种类型的错误很常见。

```Output
error C2664: 'int wsprintfW(LPWSTR,LPCWSTR,...)': cannot convert argument 1 from 'CHAR [16]' to 'LPWSTR'
```

以下是产生此错误的代码示例：

```cpp
wsprintf(szTmp, "%d.%2.2d.%4.4d", rmj, rmm, rup);
```

我们将 \_T 放在该字符串文本周围以删除此错误。

```cpp
wsprintf(szTmp, _T("%d.%2.2d.%4.4d"), rmj, rmm, rup);
```

\_T 宏可以使字符串文本编译为 char 字符串或 wchar_t 字符串，具体取决于 MBCS 或 UNICODE 的设置。 要在 Visual Studio 中将所有字符串替换为 \_T，首先需要打开“快速替换”框（键盘：Ctrl+F）或“在文件中替换”（键盘：Ctrl+Shift+H），然后选中“使用正则表达式”复选框。 输入 `((\".*?\")|('.+?'))` 作为搜索文本，输入 `_T($1)` 作为替换文本。 如果某些字符串周围已存在 \_T 宏，此过程将重新添加该宏，并且可能还会发现不需要 \_T 的情况（例如使用 `#include` 时），因此最好使用“替换下一个”而不是“全部替换”。

此特定函数 [wsprintf](/windows/desktop/api/winuser/nf-winuser-wsprintfa) 实际上在 Windows 标头中已定义，相关文档建议不使用此函数，因为可能会发生缓冲区溢出。 `szTmp` 缓冲区未给定大小，因此函数无法检查该缓冲区是否可容纳要写入的所有数据。 请参阅下一节有关移植到安全 CRT 的内容，我们将在下一节修复其他类似的问题。 最终使用 [_stprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) 进行替换。

这是转换为 Unicode 时的另一个常见错误。

```Output
error C2440: '=': cannot convert from 'char *' to 'TCHAR *'
```

生成此错误的代码如下所示：

```cpp
pParentNode->m_szText = new char[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

尽管使用了 `_tcscpy` 函数（复制字符串的 TCHAR strcpy 函数），但已分配的缓冲区是 char 缓冲区。 可轻松更改为 TCHAR。

```cpp
pParentNode->m_szText = new TCHAR[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

同样，当编译器错误保证时，我们分别将 LPSTR（指向字符串的长指针）和 LPCSTR（指向常量字符串的长指针）更改为了 LPTSTR（指向 TCHAR 字符串的长指针）和 LPCTSTR（指向常量 TCHAR 字符串的长指针）。 我们选择不使用全局搜索和替换来进行此类替换，因为必须逐个检查每种情况。 在某些情况下，需要 char 版本，如处理某些使用具有 A 后缀的 Windows 结构的 Windows 消息时。 在 Windows API 中，后缀 A 意味着 ASCII 或 ANSI（也适用于 MBCS)，而后缀 W 意味着宽字符或 UTF-16 Unicode。 此命名模式在 Windows 头文件使用，但当我们不得不添加 Unicode 版本的函数（仅在 MBCS 版本中定义）时，也将在 Spy++ 代码中进行沿用。

某些情况下，我们必须替换类型以使用正确解析的版本（例如 WNDCLASS 而非 WNDCLASSA)。

在许多情况下，必须使用 Win32 API 的通用版本（宏），如 `GetClassName`（而不是 `GetClassNameA`）。 在消息处理程序 switch 语句中，某些消息特定于 MBCS 或 Unicode，在这些情况下，必须更改代码以显式调用 MBCS 版本，因为已将常规命名的函数替换为了具有 A 和 W 后缀的特定函数，并添加了通用名称的宏，该名称可基于是否定义了 UNICODE 来解析为正确的 A 或 W 名称。  在代码的许多部分，当切换到定义 \_UNICODE 时，即使需要 A 版本，现在也会选择 W 版本。

有几个地方必须采用特殊的操作。 任何对 `WideCharToMultiByte` 或 `MultiByteToWideChar` 的使用都可能需要进行详细了解。 以下是使用 `WideCharToMultiByte` 的一个示例。

```cpp
BOOL C3dDialogTemplate::GetFont(CString& strFace, WORD& nFontSize)
{
  ASSERT(m_hTemplate != NULL);

  DLGTEMPLATE* pTemplate = (DLGTEMPLATE*)GlobalLock(m_hTemplate);
  if ((pTemplate->style & DS_SETFONT) == 0)
  {
    GlobalUnlock(m_hTemplate);
    return FALSE;
  }

  BYTE* pb = GetFontSizeField(pTemplate);
  nFontSize = *(WORD*)pb;
  pb += sizeof (WORD);
  WideCharToMultiByte(CP_ACP, 0, (LPCWSTR)pb, -1,
  strFace.GetBufferSetLength(LF_FACESIZE), LF_FACESIZE, NULL, NULL);
  strFace.ReleaseBuffer();
  GlobalUnlock(m_hTemplate);
  return TRUE;
}
```

若要解决此问题，必须了解使用它的原因在于，需要将表示字体名称的宽字符字符串复制到 `CString`、`strFace` 的内部缓冲区。 多字节 `CString` 字符串需要的代码与宽字符 `CString` 字符串稍有不同，因此我们在此案例种添加了 `#ifdef`。

```cpp
#ifdef _MBCS
WideCharToMultiByte(CP_ACP, 0, (LPCWSTR)pb, -1,
strFace.GetBufferSetLength(LF_FACESIZE), LF_FACESIZE, NULL, NULL);
strFace.ReleaseBuffer();
#else
wcscpy(strFace.GetBufferSetLength(LF_FACESIZE), (LPCWSTR)pb);
strFace.ReleaseBuffer();
#endif
```

当然，应使用更安全的版本 `wcscpy_s`而非 `wcscpy`。 下一节将解决此问题。

作为操作检查，我们应将“字符集”重置为“使用多字节字符集”，并确保代码仍使用 MBCS 和 Unicode 进行编译。 当然，发生所有这些更改后，应在重新编译的应用上执行完整的测试轮次。

在使用此 Spy++ 解决方案的工作中，对于普通 C++ 开发人员而言，将代码转换为 Unicode 大约需要两天的工作时间。 这并不包括再测试的时间。

##  <a name="porting_to_secure_crt"></a>步骤 12. 移植以使用安全 CRT

下一步是移植代码以使用安全版本（带 _s 后缀的版本）的 CRT 函数。 在这种情况下，常规策略是将函数替换为 _s 版本，然后通常会添加所需的附加缓冲区大小参数。 许多情况下这非常简单，因为大小是已知的。 在其他情况下，当不能立即知道大小时，则需要向正使用 CRT 函数的函数添加其他参数，或者可以检查目标缓冲区的使用情况并查看具体的适当大小限制。

Visual C++ 提供了技巧，可以更加轻松地获取代码安全而无需添加许多大小参数，添加参数是通过使用模板重载实现的。 由于这些重载都是模板，因此仅在作为 C++ 编译时可用，而作为 C 时不可用。Spyxxhk 是 C 项目，所以这个技巧不起作用。  但 pyxx 不是 C 项目，可以使用该技巧。 该技巧是在该项目每个文件中将进行编译的地方添加类似的行，例如在 stdafx.h 中：

```cpp
#define _CRT_SECURE_TEMPLATE_OVERLOADS 1
```

定义后，只要该缓冲区是一个数组而不是原始的指针，则可以从数组类型推断其大小，并用作大小参数，因此无需自己提供大小。 这样有助于减少重写代码的复杂性。 仍然必须将函数名称替换为 _s 版本，但通常可以通过搜索和替换操作实现。

某些函数的返回值已更改。 例如，`_itoa_s`（和 `_itow_s` 以及宏 `_itot_s`）返回错误代码 (`errno_t`)，而非字符串。 因此在这些情况下，必须将对 `_itoa_s` 的调用移到单独的行上，并替换为缓冲区的标识符。

一些常见的情况：对于 `memcpy`，切换到 `memcpy_s` 时，经常会添加要复制结构的大小。 同样，对于大多数字符串和缓冲区，数组或缓冲区的大小可以轻松从缓冲区的声明确定或通过查找最初分配缓冲区的位置来确定。 在某些情况下，你需要确定大的缓冲区如何实际可用，而如果正在修改的函数范围内该信息不可用，它应被添加为一个附加参数，并且应修改调用代码来提供信息。

使用这些技巧，大约只需要半日时间即可转换代码以使用安全的 CRT 函数。 如果不选择添加到模板重载，而是选择手动添加大小参数，则可能需要两倍或三倍的时间。

##  <a name="deprecated_forscope"></a>步骤 13. /Zc:forScope 已弃用

自 Visual C++ 6.0 起，编译器符合当前的标准，该标准将在循环中声明的变量的范围限制为循环的范围。 编译器选项 [/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)（项目属性中的“强制 for 循环范围中的符合性”）控制是否将其报告为错误。 我们应更新我们的代码以使其符合标准，并在循环外部添加声明。 若要避免更改代码，可以将“语言”部分的 C++ 项目属性中的设置更改为 `No (/Zc:forScope-)`。 但请记住，未来版本的 Visual C++ 中可能会删除 `/Zc:forScope-`，因此你的代码最终同样需要更改以符合标准。

这些问题的修复相对轻松，但具体取决于你的代码，此问题可能会影响大量代码。 下面是一个典型问题。

```cpp
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const
{
  for (int n = 0; mszStrings[0] != 0; n++)
  mszStrings = _tcschr(mszStrings, 0) + 1;
  return(n);
}
```

上面的代码生成错误：

```Output
'n': undeclared identifier
```

这是因为编译器已弃用允许不再符合 C++ 标准的代码的编译器选项。 在该标准中，在循环内声明一个变量会将其范围限制为仅在循环内，因此在循环外使用循环计数器的常见做法还要求将计数器的声明移到循环之外，如以下修改后的代码所示：

```cpp
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const
{
  int n;
  for (n = 0; mszStrings[0] != 0; n++)
  mszStrings = _tcschr(mszStrings, 0) + 1;
  return(n);
}
```

## <a name="summary"></a>总结

将 Spy++ 从原始的 Visual C++ 6.0 代码移植到最新的编译器需要花费大约 20 个小时的编码时间，历经一周的过程。 我们跳过了该产品的 8 个版本（从 Visual Studio 6.0 到 Visual Studio 2015）直接升级。 现在，这是所有大小型项目升级的推荐方法。

## <a name="see-also"></a>请参阅

[移植和升级：示例和案例研究](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[上一个案例研究：COM Spy](../porting/porting-guide-com-spy.md)

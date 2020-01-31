---
title: 更新 WINVER 和 _WIN32_WINNT
description: 何时以及如何更新升级的 Visual Studio C++项目中的 WINVER 和 _WIN32_WINNT 宏。
ms.date: 01/22/2020
helpviewer_keywords:
- WINVER in an upgraded Visual Studio C++ project
- _WIN32_WINNT in an upgraded Visual Studio C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
ms.openlocfilehash: b81c7967732c7b0c23ff0eb73d2a866a9b33713b
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725691"
---
# <a name="update-winver-and-_win32_winnt"></a>更新 WINVER 和 _WIN32_WINNT

当你使用 Windows SDK 时，可以指定你的代码可在哪个版本的 Windows 上运行。 预处理器宏**WINVER**和 **_WIN32_WINNT**指定代码支持的最低操作系统版本。 Visual Studio 和 Microsoft C++编译器支持面向 WINDOWS 7 SP1 及更高版本。 旧版工具集包括对 Windows XP SP4、Windows Server 2003 SP4、Vista 和 Windows Server 2008 的支持。 不支持 windows 95、Windows 98、Windows ME、Windows NT 和 Windows 2000。

升级旧项目时，可能需要更新**WINVER**或 **_WIN32_WINNT**宏。 如果为不受支持的 Windows 版本分配值，可能会看到与这些宏相关的编译错误。

## <a name="remarks"></a>备注

若要修改宏，请在标头文件中（例如，在*targetver.h*中，它由面向 Windows 的某些项目模板包含）添加以下行。

```C
#define WINVER 0x0A00
#define _WIN32_WINNT 0x0A00
```

示例中的宏设置为面向每个版本的 Windows 10 操作系统。 可能的值列在 Windows 头文件*sdkddkver.h*中，该文件为每个主要 Windows 版本定义宏。 若要生成应用程序以支持以前的 Windows 平台，请包含*winsdkver.h*。 然后，将**WINVER**和 **_WIN32_WINNT**宏设置为最早的支持平台，然后再包括*sdkddkver.h*。 下面是*sdkddkver.h*的 WINDOWS 10 SDK 版本中的行，它对每个主版本的 windows 的值进行编码：

```C
//
// _WIN32_WINNT version constants
//
#define _WIN32_WINNT_NT4                    0x0400 // Windows NT 4.0
#define _WIN32_WINNT_WIN2K                  0x0500 // Windows 2000
#define _WIN32_WINNT_WINXP                  0x0501 // Windows XP
#define _WIN32_WINNT_WS03                   0x0502 // Windows Server 2003
#define _WIN32_WINNT_WIN6                   0x0600 // Windows Vista
#define _WIN32_WINNT_VISTA                  0x0600 // Windows Vista
#define _WIN32_WINNT_WS08                   0x0600 // Windows Server 2008
#define _WIN32_WINNT_LONGHORN               0x0600 // Windows Vista
#define _WIN32_WINNT_WIN7                   0x0601 // Windows 7
#define _WIN32_WINNT_WIN8                   0x0602 // Windows 8
#define _WIN32_WINNT_WINBLUE                0x0603 // Windows 8.1
#define _WIN32_WINNT_WINTHRESHOLD           0x0A00 // Windows 10
#define _WIN32_WINNT_WIN10                  0x0A00 // Windows 10
```

对于更细化的版本控制方法，可以使用*sdkddkver.h*中的 NTDDI 版本常量。 下面是 Windows 10 SDK 版本10.0.18362.0 中*sdkddkver.h*定义的一些宏：

```C
//
// NTDDI version constants
//
#define NTDDI_WIN7                          0x06010000
#define NTDDI_WIN8                          0x06020000
#define NTDDI_WINBLUE                       0x06030000
#define NTDDI_WINTHRESHOLD                  0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10                         0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10_TH2                     0x0A000001  /* ABRACADABRA_WIN10_TH2 */
#define NTDDI_WIN10_RS1                     0x0A000002  /* ABRACADABRA_WIN10_RS1 */
#define NTDDI_WIN10_RS2                     0x0A000003  /* ABRACADABRA_WIN10_RS2 */
#define NTDDI_WIN10_RS3                     0x0A000004  /* ABRACADABRA_WIN10_RS3 */
#define NTDDI_WIN10_RS4                     0x0A000005  /* ABRACADABRA_WIN10_RS4 */
#define NTDDI_WIN10_RS5                     0x0A000006  /* ABRACADABRA_WIN10_RS5 */
#define NTDDI_WIN10_19H1                    0x0A000007  /* ABRACADABRA_WIN10_19H1*/

#define WDK_NTDDI_VERSION                   NTDDI_WIN10_19H1 /* ABRACADABRA_WIN10_19H1 */

//
// masks for version macros
//
#define OSVERSION_MASK      0xFFFF0000
#define SPVERSION_MASK      0x0000FF00
#define SUBVERSION_MASK     0x000000FF

//
// macros to extract various version fields from the NTDDI version
//
#define OSVER(Version)  ((Version) & OSVERSION_MASK)
#define SPVER(Version)  (((Version) & SPVERSION_MASK) >> 8)
#define SUBVER(Version) (((Version) & SUBVERSION_MASK) )
```

可以在代码中使用**OSVER**、 **SPVER**和**SUBVER**宏来控制不同级别的 API 支持的条件编译。

你可能看不到所要查看的*sdkddkver.h*中列出的所有 Windows 版本。 这意味着你可能使用的是较旧版本的 Windows SDK。 默认情况下，Visual Studio 中的新 Windows 项目使用 Windows 10 SDK。

> [!NOTE]
> 如果将内部 MFC 头文件包含到应用程序中，则无法保证这些值有效。

你还可以使用 `/D` 编译器选项定义此宏。 有关详细信息，请参阅 [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md)。

若要深入了解这些宏的含义，请参阅 [使用 Windows 头文件](/windows/win32/WinProg/using-the-windows-headers)。

## <a name="see-also"></a>另请参阅

[Visual C++ 更改历史记录](../porting/visual-cpp-change-history-2003-2015.md)

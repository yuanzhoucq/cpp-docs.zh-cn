---
title: 链接器工具警告 LNK4210
ms.date: 11/04/2016
f1_keywords:
- LNK4210
helpviewer_keywords:
- LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
ms.openlocfilehash: 75376129ce0033c717a4da3074cee9de132d357d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395061"
---
# <a name="linker-tools-warning-lnk4210"></a>链接器工具警告 LNK4210

> 部分*部分*存在; 那里可能未经处理的静态初始值设定项或结束符

## <a name="remarks"></a>备注

静态初始值设定项或结束符，引入了一些代码，但 VCRuntime 库启动代码或其等效项 （需要运行静态初始值设定项或结束符） 应用程序启动时没有运行。 下面是代码的需要静态初始值设定项或终止符的一些示例：

- 全局类具有构造函数、 析构函数或虚函数表的变量。

- 使用非编译时常量进行初始化的全局变量。

若要解决此问题，请尝试以下项之一：

- 使用静态初始值设定项中删除所有代码。

- 不要使用[/NOENTRY](../../build/reference/noentry-no-entry-point.md)。 删除 /NOENTRY 后，可能需要删除[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)从链接器命令行。

- 如果你的生成使用 /MT，添加到链接器命令行 libcmt.lib、 libvcruntime.lib 和 libucrt.lib。 如果你的生成使用 /MTd，添加 libcmtd.lib、 vcruntimed.lib 和 libucrtd.lib。

- 时从 /clr: pure 编译为 /clr，删除[/ENTRY](../../build/reference/entry-entry-point-symbol.md)从链接器行的选项。 这使 CRT 初始化，并允许在应用程序启动时要执行的静态初始值设定项。 **/Clr: pure**编译器选项在 Visual Studio 2015 中弃用并在 Visual Studio 2017 中不受支持。

[/GS](../../build/reference/gs-buffer-security-check.md)编译器选项需要通过初始化`__security_init_cookie`函数。 默认情况下，在运行在 VCRuntime 库启动代码中提供此初始化`_DllMainCRTStartup`。

- 如果使用 /ENTRY，生成你的项目和 /ENTRY 而不传递一个函数`_DllMainCRTStartup`，该函数必须调用`_CRT_INIT`初始化 CRT。 如果 DLL 使用 /GS、 需要静态初始值设定项，或在 MFC 或 ATL 代码的上下文中调用此单独的调用是不够的。 请参阅[Dll 和 VisualC++运行时库行为](../../build/run-time-library-behavior.md)有关详细信息。

## <a name="see-also"></a>请参阅

- [设置链接器选项](../../build/reference/linking.md)

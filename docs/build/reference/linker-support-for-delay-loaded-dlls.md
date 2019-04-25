---
title: 链接器的延迟加载 DLL 支持
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
ms.openlocfilehash: b6e514a6b13aced4fcd765df091810504f948588
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176247"
---
# <a name="linker-support-for-delay-loaded-dlls"></a>链接器的延迟加载 DLL 支持

MSVC 链接器现在支持 Dll 的延迟的加载。 这使你的需要使用 Windows SDK 函数**LoadLibrary**并**GetProcAddress**来实现延迟加载的 DLL。

视觉对象之前C++6.0，在运行时加载 DLL 的唯一方法是通过使用**LoadLibrary**并**GetProcAddress**; 操作系统将加载 DLL 时可执行文件或 DLL 使用已加载。

从开始 Visual C++ 6.0，隐式链接与 DLL 时，链接器提供了选项要延迟加载 DLL 直到程序调用一个函数，该 DLL 中。

应用程序可能会延迟加载 DLL 使用[/DELAYLOAD （延迟加载导入）](delayload-delay-load-import.md)帮助程序函数使用链接器选项 (默认实现提供视觉对象的C++)。 帮助器函数将加载 DLL 在运行时通过调用**LoadLibrary**并**GetProcAddress**为您。

应考虑延迟加载 DLL，如果：

- 您的程序可能会在 DLL 中调用的函数。

- 不可能获取 DLL 中的函数调用之前较晚的程序的执行。

DLL 的延迟的加载可以指定的生成过程。EXE 或。DLL 项目。 答:。延迟的一个或多个 Dll 加载的 DLL 项目不应自行调用延迟加载的入口点位于 Dllmain 中。

以下主题介绍了延迟加载 Dll:

- [指定要延迟加载的 DLL](specifying-dlls-to-delay-load.md)

- [显式卸载延迟加载的 DLL](explicitly-unloading-a-delay-loaded-dll.md)

- [加载被延迟加载的 DLL 的所有导入](loading-all-imports-for-a-delay-loaded-dll.md)

- [绑定导入](binding-imports.md)

- [错误处理和通知](error-handling-and-notification.md)

- [转储延迟加载的导入](dumping-delay-loaded-imports.md)

- [延迟加载 DLL 的约束](constraints-of-delay-loading-dlls.md)

- [了解 Helper 函数](understanding-the-helper-function.md)

- [开发自己的 Helper 函数](developing-your-own-helper-function.md)

## <a name="see-also"></a>请参阅

[Visual C++ 中的 DLL](../dlls-in-visual-cpp.md)<br/>
[MSVC 链接器参考](linking.md)

---
title: LoadLibrary 和 AfxLoadLibrary
description: 使用 LoadLibrary 和 AfxLoadLibrary 在 MSVC 中显式加载 Dll。
ms.date: 01/28/2020
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: f803212c4485f7517dc42802f1ff581ffa4e609d
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821533"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary 和 AfxLoadLibrary

处理调用[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)或[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)以显式链接到 DLL。 （MFC 应用程序使用[AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)或[AfxLoadLibraryEx](../mfc/reference/application-information-and-management.md#afxloadlibraryex)。）如果该函数成功，它会将指定的 DLL 映射到调用进程的地址空间中，并返回 DLL 的句柄。 用于显式链接的其他函数（例如 `GetProcAddress` 和 `FreeLibrary`）需要句柄。 有关详细信息，请参阅[显式链接](linking-an-executable-to-a-dll.md#linking-explicitly)。

`LoadLibrary` 尝试使用用于隐式链接的相同搜索序列来查找 DLL。 `LoadLibraryEx` 使你可以更好地控制搜索路径顺序。 有关详细信息，请参阅[动态链接库搜索顺序](/windows/win32/dlls/dynamic-link-library-search-order)。 如果系统找不到 DLL 或入口点函数返回 FALSE，`LoadLibrary` 将返回 NULL。 如果对 `LoadLibrary` 的调用指定已映射到调用进程的地址空间中的 DLL 模块，则该函数将返回该 DLL 的句柄并递增该模块的引用计数。

如果 DLL 具有入口点函数，则操作系统会在调用 `LoadLibrary` 或 `LoadLibraryEx`的线程的上下文中调用函数。 如果 DLL 已附加到进程，则不会调用入口点函数。 如果对 DLL 的 `LoadLibrary` 或 `LoadLibraryEx` 的上一次调用没有相应的 `FreeLibrary` 函数调用，就会发生这种情况。

对于加载 MFC 扩展 Dll 的 MFC 应用程序，我们建议使用 `AfxLoadLibrary` 或 `AfxLoadLibraryEx`，而不是 `LoadLibrary` 或 `LoadLibraryEx`。 在显式加载 DLL 之前，MFC 函数将处理线程同步。 要 `AfxLoadLibrary` 和 `AfxLoadLibraryEx` 的接口（函数原型）与 `LoadLibrary` 和 `LoadLibraryEx`相同。

如果 Windows 无法加载 DLL，则进程可能会尝试从错误中恢复。 例如，它可能会向用户通知错误，并请求其他 DLL 的路径。

> [!IMPORTANT]
> 请确保指定任意 Dll 的完整路径。 `LoadLibrary`加载文件时，可以先搜索当前目录。 如果未完全限定文件的路径，则可能会加载一个非目标文件。 创建 DLL 时，请使用[/DEPENDENTLOADFLAG](reference/dependentloadflag.md)链接器选项指定静态链接的 dll 依赖项的搜索顺序。 在 Dll 中，使用显式加载的依赖项的完整路径，并 `LoadLibraryEx` 或 `AfxLoadLibraryEx` 调用参数来指定模块搜索顺序。 有关详细信息，请参阅[动态链接库安全性](/windows/win32/dlls/dynamic-link-library-security)和[动态链接库搜索顺序](/windows/win32/dlls/dynamic-link-library-search-order)。

## <a name="what-do-you-want-to-do"></a>要执行什么操作Јї

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [动态链接库搜索顺序](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary 和 AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>另请参阅

- [在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)

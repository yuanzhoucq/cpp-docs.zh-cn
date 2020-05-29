---
title: LoadLibrary 和 AfxLoadLibrary
description: 使用 LoadLibrary 和 AfxLoadLibrary 在 MSVC 中显式加载 DLL。
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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821533"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary 和 AfxLoadLibrary

进程调用 [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) 或 [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) 以显式链接到 DLL。 （MFC 应用使用 [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary) 或 [AfxLoadLibraryEx](../mfc/reference/application-information-and-management.md#afxloadlibraryex)。）如果函数执行成功，它会将指定的 DLL 映射到调用进程的地址空间中并返回该 DLL 的句柄。 此句柄可以与其他函数（如 `GetProcAddress` 和 `FreeLibrary`）一起在显式链接中使用。 有关详细信息，请参阅[显示链接](linking-an-executable-to-a-dll.md#linking-explicitly)。

`LoadLibrary` 将尝试使用用于隐式链接的相同搜索顺序来查找 DLL。 `LoadLibraryEx` 使你可以更好地控制搜索路径顺序。 有关详细信息，请参阅[动态链接库搜索顺序](/windows/win32/dlls/dynamic-link-library-search-order)。 如果系统找不到 DLL 或如果入口点函数返回 FALSE，则 `LoadLibrary` 将返回 NULL。 如果对 `LoadLibrary` 的调用所指定的 DLL 模块已映射到调用进程地址空间中，则该函数将返回 DLL 的句柄并递增模块的引用数。

如果 DLL 具有入口点函数，则操作系统将在调用 `LoadLibrary` 或 `LoadLibraryEx` 的线程的上下文中调用此函数。 如果 DLL 已附加到进程中，则不会调用此入口点函数。 此情况是由于以前调用 DLL 的 `LoadLibrary` 或 `LoadLibraryEx` 函数时没有相应地调用 `FreeLibrary` 函数。

对于加载 MFC 扩展 DLL 的 MFC 应用程序，我们建议你使用 `AfxLoadLibrary` 或 `AfxLoadLibraryEx`，而不是 `LoadLibrary` 或 `LoadLibraryEx`。 MFC 函数会在显示加载 DLL 前处理线程同步。 `AfxLoadLibrary` 和 `AfxLoadLibraryEx` 的接口（函数原型）与 `LoadLibrary` 和 `LoadLibraryEx` 相同。

如果 Windows 无法加载 DLL，则进程会尝试从错误中恢复。 例如，进程会通知用户所发生的错误，并让用户指定 DLL 的其他路径。

> [!IMPORTANT]
> 请确保指定任何 DLL 的完整路径。 `LoadLibrary` 加载文件时可能会首先搜索当前目录。 如果不完全限定文件的路径，则可能会加载一个非目标文件。 创建 DLL 时，请使用 [/DEPENDENTLOADFLAG](reference/dependentloadflag.md) 链接器选项来指定静态链接的 DLL 依赖项的搜索顺序。 在 DLL 中，使用显式加载的依赖项和 `LoadLibraryEx` 或 `AfxLoadLibraryEx` 调用参数的完整路径指定模块搜索顺序。 有关详细信息，请参阅[动态链接库安全](/windows/win32/dlls/dynamic-link-library-security)和[动态链接库搜索顺序](/windows/win32/dlls/dynamic-link-library-search-order)。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [动态链接库搜索顺序](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary 和 AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>请参阅

- [在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)

---
title: LoadLibrary 和 AfxLoadLibrary
ms.date: 05/24/2018
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: c7700dd865e320686a2ad8bd036f207b9ecee6ac
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493213"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary 和 AfxLoadLibrary

处理调用[LoadLibraryExA](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa)或[LoadLibraryExW](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) (或[AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) 以显式链接到 DLL。 如果该函数成功, 它会将指定的 DLL 映射到调用进程的地址空间中, 并返回 DLL 的句柄, 该句柄可用于显式链接中的其他函数, `GetProcAddress`例如`FreeLibrary`和。

`LoadLibrary`尝试使用用于隐式链接的相同搜索序列来查找 DLL。 如果系统找不到 DLL 或入口点函数返回 FALSE, `LoadLibrary`则返回 NULL。 如果调用`LoadLibrary`指定的 dll 模块已映射到调用进程的地址空间, 则该函数将返回该 dll 的句柄并递增该模块的引用计数。

如果 DLL 具有入口点函数, 则操作系统会在调用`LoadLibrary`的线程的上下文中调用函数。 如果 DLL 已附加到进程, 则不会调用入口点函数, 因为对`LoadLibrary`的前一次调用没有相应的`FreeLibrary`函数调用。

对于加载 mfc 扩展 dll 的 mfc 应用程序, 我们建议你使用`AfxLoadLibrary` `LoadLibrary`而不是。 `AfxLoadLibrary`在调用`LoadLibrary`之前处理线程同步。 与`AfxLoadLibrary`的接口 (函数原型) `LoadLibrary`相同。

如果 Windows 无法加载 DLL, 则进程可能会尝试从错误中恢复。 例如, 进程可能会向用户通知错误, 并要求用户指定 DLL 的其他路径。

> [!IMPORTANT]
> 请确保指定任意 Dll 的完整路径。 在加载文件时首先搜索当前目录。 如果未限定文件的路径, 则可能会加载不是预期的文件。 防止这种情况的另一种方法是使用[/DEPENDENTLOADFLAG](reference/dependentloadflag.md)链接器选项。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [动态链接库搜索顺序](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary 和 AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>请参阅

- [在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)

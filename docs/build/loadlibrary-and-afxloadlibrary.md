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
ms.openlocfilehash: 7c0b63d80a8b4b03b55d6e50af6c08a8de0937de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596534"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary 和 AfxLoadLibrary

处理调用[LoadLibraryExA](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)或[LoadLibraryExW](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexw)(或[AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) 以显式链接到 DLL。 如果函数成功，它将指定的 DLL 映射到调用进程的地址空间，并返回的句柄可用于在显式链接中的其他函数的 DLL — 例如，`GetProcAddress`和`FreeLibrary`。

`LoadLibrary` 尝试使用用于隐式链接的相同搜索序列来定位 DLL。 如果系统找不到 DLL 或入口点函数返回 FALSE，`LoadLibrary`返回 NULL。 如果在调用`LoadLibrary`指定已映射到调用进程的地址空间的 DLL 模块函数返回的句柄的 DLL 和增量的模块的引用计数。

如果 DLL 具有入口点函数，操作系统将调用该函数的调用的线程上下文中`LoadLibrary`。 如果 DLL 已附加到进程由于以前调用，将不会调用入口点函数`LoadLibrary`具有没有相应地调用`FreeLibrary`函数。

对于加载 MFC 扩展 Dll 的 MFC 应用程序，我们建议你使用`AfxLoadLibrary`而不是`LoadLibrary`。 `AfxLoadLibrary` 处理线程同步，然后再调用`LoadLibrary`。 接口 （函数原型） 到`AfxLoadLibrary`等同于`LoadLibrary`。

如果 Windows 无法加载 DLL，进程可以尝试从错误中恢复。 例如，进程无法通知错误的用户，要求用户指定另一个 DLL 路径。

> [!IMPORTANT]
> 请确保指定的任何 Dll 的完整路径。 加载文件时会首先搜索当前目录。 如果不符合条件的文件路径，可能会加载不是预期的文件。 若要防止这种情况的另一种方法是使用[/DEPENDENTLOADFLAG](../build/reference/dependentloadflag.md)链接器选项。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [如何隐式链接到 DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [确定要使用的链接方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [动态链接库搜索顺序](/windows/desktop/Dlls/dynamic-link-library-search-order)

- [FreeLibrary 和 AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](../build/getprocaddress.md)

## <a name="see-also"></a>请参阅

- [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)

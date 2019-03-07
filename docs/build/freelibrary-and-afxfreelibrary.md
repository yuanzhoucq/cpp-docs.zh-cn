---
title: FreeLibrary 和 AfxFreeLibrary
ms.date: 11/04/2016
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
ms.openlocfilehash: 51d14b86a92f3acb76dc54d1bade2d2cd0baa055
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419941"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary 和 AfxFreeLibrary

显式链接到 DLL 调用的进程[FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary)时不再需要 DLL 模块的功能。 此函数逐量减小模块的引用计数，如果引用计数为零，但不把它从进程的地址空间。

MFC 应用程序中使用[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)而不是`FreeLibrary`来卸载 MFC 扩展 DLL。 接口 （函数原型）`AfxFreeLibrary`等同于`FreeLibrary`。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [如何隐式链接到 DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [确定要使用的链接方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](../build/getprocaddress.md)

## <a name="see-also"></a>请参阅

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)<br/>
[FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary)
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)

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
ms.openlocfilehash: 0b530aca2ab036de186ff3fdb11be23f41e12d05
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821546"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary 和 AfxFreeLibrary

当不再需要 DLL 模块时，显式链接到 DLL 的进程将调用[FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)函数。 此函数递减模块的引用计数。 而且，如果引用计数为零，则将其从进程的地址空间取消映射。

在 MFC 应用程序中，使用[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)而不是 `FreeLibrary` 来卸载 MFC 扩展 DLL。 `AfxFreeLibrary` 的接口（函数原型）与 `FreeLibrary`相同。

## <a name="what-do-you-want-to-do"></a>要执行什么操作Јї

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [LoadLibrary 和 AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>另请参阅

[在 Visual StudioC++中创建 C/dll](dlls-in-visual-cpp.md)\
[FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)\
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)

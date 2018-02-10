---
title: "LoadLibrary 和 AfxLoadLibrary |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LoadLibrary
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd24f125398cab606ca835094727a4a2819fb17e
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary 和 AfxLoadLibrary
处理调用[LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187) (或[AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) 显式链接到 DLL。 如果函数成功，它将指定的 DLL 映射到调用进程的地址空间，并可与其他函数中显式链接的 DLL 中返回的句柄 — 例如，`GetProcAddress`和`FreeLibrary`。  
  
 `LoadLibrary`尝试通过使用相同的搜索序列用于隐式链接定位 DLL。 如果系统找不到 DLL 或入口点函数返回 FALSE，`LoadLibrary`返回 NULL。 如果调用`LoadLibrary`指定 DLL 模块已映射到的地址空间的调用的过程中，该函数返回的句柄的 DLL 和增量模块的引用计数。  
  
 如果 DLL 具有一个入口点函数，则操作系统调用的函数调用的线程的上下文中`LoadLibrary`。 如果 DLL 已因以前调用而附加到进程，将不会调用入口点函数`LoadLibrary`具有没有相应地调用`FreeLibrary`函数。  
  
 对于负载 MFC 扩展 Dll 的 MFC 应用程序，我们建议你使用`AfxLoadLibrary`而不是`LoadLibrary`。 `AfxLoadLibrary`处理线程同步，然后才能调用`LoadLibrary`。 接口 （函数原型）`AfxLoadLibrary`相同`LoadLibrary`。  
  
 如果 Windows 无法加载 DLL，该过程可以尝试从错误中恢复。 例如，进程无法通知错误的用户并要求用户指定的 DLL 的另一个路径。  
  
> [!IMPORTANT]
>  请确保指定的任何 Dll 的完整路径。 已加载文件时，将首先搜索当前目录。 如果不符合的文件的路径，则可能会加载不是预期的文件。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [如何将隐式链接到 DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [确定要使用的链接方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [Windows 用来定位 DLL 搜索路径](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
-   [FreeLibrary 和 AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## <a name="see-also"></a>请参阅  
 [Visual c + + 中的 Dll](../build/dlls-in-visual-cpp.md)   
 [LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187)   
 [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)
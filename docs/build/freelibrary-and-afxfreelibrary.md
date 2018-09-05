---
title: FreeLibrary 和 AfxFreeLibrary |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
dev_langs:
- C++
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 063c858253c12cfedbf252a124029b8cbc16a691
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680958"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary 和 AfxFreeLibrary
显式链接到 DLL 调用的进程[FreeLibrary](https://msdn.microsoft.com/library/windows/desktop/ms683152(v=vs.85).aspx)时不再需要 DLL 模块的功能。 此函数逐量减小模块的引用计数，如果引用计数为零，但不把它从进程的地址空间。  
  
 MFC 应用程序中使用[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)而不是`FreeLibrary`来卸载 MFC 扩展 DLL。 接口 （函数原型）`AfxFreeLibrary`等同于`FreeLibrary`。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [如何隐式链接到 DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [确定要使用的链接方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## <a name="see-also"></a>请参阅  
 [Visual c + + 中的 Dll](../build/dlls-in-visual-cpp.md)   
 [FreeLibrary](https://msdn.microsoft.com/library/windows/desktop/ms683152(v=vs.85).aspx)   
 [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)
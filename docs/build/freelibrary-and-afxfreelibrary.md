---
title: "FreeLibrary 和 AfxFreeLibrary | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FreeLibrary"
  - "AfxFreeLibrary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "扩展 DLL [C++], 卸载"
  - "AfxFreeLibrary 方法"
  - "卸载 DLL"
  - "FreeLibrary 方法"
  - "DLL [C++], 链接"
  - "显式链接 [C++]"
  - "DLL [C++], 卸载"
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# FreeLibrary 和 AfxFreeLibrary
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不再需要 DLL 模块时，显式链接到 DLL 的进程调用 [FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188) 函数。  此函数递减模块的引用数，如果引用数为零，此函数便从进程的地址空间中取消模块的映射。  
  
 在 MFC 应用程序中，使用 [AfxFreeLibrary](../Topic/AfxFreeLibrary.md) 而非 `FreeLibrary` 来卸载扩展 DLL。  `AfxFreeLibrary` 的接口（函数原型）与 `FreeLibrary` 相同。  
  
## 你希望做什么？  
  
-   [隐式链接](../build/linking-implicitly.md)  
  
-   [确定要使用的链接方法](../build/determining-which-linking-method-to-use.md)  
  
## 您想进一步了解什么？  
  
-   [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)   
 [FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)   
 [AfxFreeLibrary](../Topic/AfxFreeLibrary.md)
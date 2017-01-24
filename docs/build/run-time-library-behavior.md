---
title: "运行库行为 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_DllMainCRTStartup"
  - "CRT_INIT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CRT_INIT 宏"
  - "_DllMainCRTStartup 方法"
  - "DllMain 函数"
  - "DLL [C++], 入口点函数"
  - "DLL [C++], 运行库行为"
  - "DLL [C++], 启动顺序"
  - "进程附加 [C++]"
  - "进程分离 [C++]"
  - "运行时 [C++], DLL 启动顺序"
ms.assetid: e06f24ab-6ca5-44ef-9857-aed0c6f049f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 运行库行为
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\/C\+\+ 运行库代码执行 DLL 启动序列，从而不必像 Windows 3.x 中那样必须链接到单独的模块。  C\/C\+\+ 运行库代码中包含的是名为 **\_DllMainCRTStartup** 的 DLL 入口点函数。  **\_DllMainCRTStartup** 函数执行若干操作，其中包括调用 **\_CRT\_INIT**，此操作初始化 C\/C\+\+ 运行库并在静态非局部变量上调用 C\+\+ 构造函数。  如果没有此函数，运行库将保持未初始化状态。  **\_CRT\_INIT** 既可以用于静态链接的 CRT，也可以从用户 DLL 链接到 CRT DLL Msvcr90.dll。  
  
 虽然可以使用 \/ENTRY: 链接器选项指定其他入口点函数，但不建议这样做，因为新的入口点函数将不得不重复 **\_DllMainCRTStartup** 执行的所有操作。  用 Visual C\+\+ 生成 DLL 时，系统自动链接 **\_DllMainCRTStartup**，您无需使用 \/ENTRY: 链接器选项指定入口点函数。  
  
 除了初始化 C 运行库外，**\_DllMainCRTStartup** 还调用名为 `DllMain` 的函数。  根据生成的 DLL 类型的不同，Visual C\+\+ 为您提供 `DllMain` 并使它被链接，以便 **\_DllMainCRTStartup** 始终有东西可以调用。  这样，如果不需要初始化 DLL，则在生成 DLL 时没有什么特别的事情要做。  如果需要初始化 DLL，添加代码的位置取决于编写的 DLL 类型。  有关更多信息，请参见[初始化 DLL](../build/initializing-a-dll.md)。  
  
 C\/C\+\+ 运行库代码在静态非局部变量上调用构造函数和析构函数。  例如，在以下 DLL 源代码中，`Equus` 和 `Sugar` 是 `CHorse` 类的两个静态非本地对象，它们都是在 Horses.h 中定义的。  源代码中没有任何函数包含对 `CHorse` 的构造函数或析构函数的调用，因为这些对象是在这些函数的外部定义的。  因此，必须由运行时代码执行对这些构造函数和析构函数的调用。  应用程序的运行库代码也执行此函数。  
  
```  
#include "horses.h"  
  
CHorse  Equus( ARABIAN, MALE );  
CHorse  Sugar( THOROUGHBRED, FEMALE );  
  
BOOL    WINAPI   DllMain (HANDLE hInst,   
                            ULONG ul_reason_for_call,  
                            LPVOID lpReserved)  
...  
```  
  
 每当新进程尝试使用 DLL 时，操作系统就为 DLL 数据创建一个单独的副本：这称作“进程附加”。  DLL 的运行库代码调用所有全局对象的构造函数（如果有的话），然后通过选定进程附加来调用 `DllMain` 函数。  相反的情况是线程分离：运行库代码通过选定进程分离来调用 `DllMain`，然后调用一系列终止函数，其中包括 `atexit` 函数、全局对象的析构函数和静态对象的析构函数。  请注意，进程附加中的事件顺序与进程分离中的相反。  
  
 线程附加和线程分离时也会调用运行库代码，但是运行库代码不主动执行任何初始化和终止操作。  
  
## 你希望做什么？  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)
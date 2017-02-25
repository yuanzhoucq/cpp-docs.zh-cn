---
title: "通知挂钩 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL 的延迟加载, 通知挂钩"
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 通知挂钩
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

只有当在 Helper 例程中执行下列操作之前才调用通知挂钩：  
  
-   检查存储的库句柄，确保已经加载。  
  
-   调用 **LoadLibrary** 以尝试加载 DLL。  
  
-   调用 **GetProcAddress** 以尝试获取过程地址。  
  
-   返回到延迟导入加载 thunk。  
  
 用下列方法启用通知挂钩：  
  
-   通过提供指针 **\_\_pfnDliNotifyHook2** 的新定义，该指针已初始化为指向您自己的接收通知的函数。  
  
     \- 或 \-  
  
-   通过在调用程序正在延迟加载的 DLL 之前设置指向挂钩函数的指针 **\_\_pfnDliNotifyHook2**。  
  
 如果通知是 **dliStartProcessing**，则挂钩函数可以返回：  
  
 NULL  
 默认 Helper 处理 DLL 加载。  若只是为了了解信息，那么调用它是很有用的。  
  
 函数指针  
 跳过默认的延迟加载处理。  这使您能够提供自己的加载处理程序。  
  
 如果通知是 **dliNotePreLoadLibrary**，挂钩函数可以返回：  
  
-   0，如果只需要信息性通知。  
  
-   已加载的 DLL 的 HMODULE，如果它自己加载了 DLL 的话。  
  
 如果通知是 **dliNotePreGetProcAddress**，挂钩函数可以返回：  
  
-   0，如果只需要信息性通知。  
  
-   已导入函数的地址，如果挂钩函数自已获取地址的话。  
  
 如果通知是 **dliNoteEndProcessing**，挂钩函数的返回值将忽略。  
  
 若该指针已初始化（非零），延迟加载 Helper 在执行过程中将在某些通知点调用此函数。  该函数指针具有如下定义：  
  
```  
// The "notify hook" gets called for every call to the  
// delay load helper.  This allows a user to hook every call and  
// skip the delay load helper entirely.  
//  
// dliNotify == {  
//  dliStartProcessing |  
//  dliNotePreLoadLibrary  |  
//  dliNotePreGetProc |  
//  dliNoteEndProcessing}  
//  on this call.  
//  
ExternC  
PfnDliHook   __pfnDliNotifyHook2;  
  
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}  
ExternC  
PfnDliHook   __pfnDliFailureHook2;  
```  
  
 在 **DelayLoadInfo** 结构中，通知连同通知值一起传递给挂钩函数。  该数据与延迟加载 Helper 例程使用的数据相同。  通知值将为[结构和常数定义](../../build/reference/structure-and-constant-definitions.md)中定义的值之一。  
  
## 请参阅  
 [错误处理和通知](../../build/reference/error-handling-and-notification.md)
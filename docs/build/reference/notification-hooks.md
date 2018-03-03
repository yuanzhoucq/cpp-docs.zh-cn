---
title: "通知挂钩 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, notification hooks
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 31490e3bb591af6568ffecddf68219c89a25e055
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="notification-hooks"></a>通知挂钩
通知挂钩调用之前在 helper 例程执行以下操作：  
  
-   库的存储句柄检查以确定已加载。  
  
-   **LoadLibrary**称为尝试加载的 DLL。  
  
-   **GetProcAddress**称为尝试获得的过程的地址。  
  
-   返回到延迟导入负载转换 （thunk）。  
  
 启用通知挂钩：  
  
-   通过提供新的定义的指针**__pfnDliNotifyHook2**被初始化为指向您自己的函数，它接收通知。  
  
     或  
  
-   通过设置指针**__pfnDliNotifyHook2**到挂钩函数之前调用的程序的 DLL 延迟加载。  
  
 如果通知为**dliStartProcessing**，挂钩函数可以返回：  
  
 NULL  
 默认帮助器处理加载的 DLL。 这可用于调用只是用于信息说明。  
  
 函数指针  
 绕过默认延迟加载处理。 这允许你提供你自己负载的处理程序。  
  
 如果通知为**dliNotePreLoadLibrary**，挂钩函数可以返回：  
  
-   如果为 0，它只是想条信息性通知。  
  
-   对于加载 DLL，如果它加载 DLL 本身 HMODULE。  
  
 如果通知为**dliNotePreGetProcAddress**，挂钩函数可以返回：  
  
-   如果为 0，它只是想条信息性通知。  
  
-   导入的函数的地址，如果挂钩函数获取本身的地址。  
  
 如果通知为**dliNoteEndProcessing**，挂钩函数的返回值将被忽略。  
  
 如果此指针进行初始化 （非零），延迟加载 helper 将调用此函数在其执行中的某些通知点。 函数指针具有以下定义：  
  
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
  
 通知传入**DelayLoadInfo**挂钩函数以及通知值结构。 此数据等同于使用的延迟加载 helper 例程。 通知值将为中定义的值之一[结构和常量定义](../../build/reference/structure-and-constant-definitions.md)。  
  
## <a name="see-also"></a>请参阅  
 [错误处理和通知](../../build/reference/error-handling-and-notification.md)
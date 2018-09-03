---
title: C 运行时错误 R6016 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6016
dev_langs:
- C++
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f366ceff24ce65e6f7869f9709f547651687c327
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33306929"
---
# <a name="c-runtime-error-r6016"></a>C 运行时错误 R6016
线程数据所需的空间不足  
  
> [!NOTE]
>  如果你在上运行应用程序时遇到此错误消息，应用程序关闭，因为它存在内部内存问题。 有许多可能的原因，对于此错误，但通常因为通过极低的内存不足，在应用中，bug 或中的 bug 或使用应用程序的扩展插件。  
>   
>  可以尝试以下步骤来修复此错误：  
>   
>  -   关闭其他正在运行的应用程序或重新启动计算机以释放内存。  
> -   使用**的应用和功能**或**程序和功能**页面**控制面板**来修复或重新安装该应用。  
> -   使用**的应用和功能**或**程序和功能**页面**控制面板**删除、 修复或重新安装外接程序或应用程序所使用的扩展。  
> -   检查**Windows Update**中**控制面板**软件更新。  
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。  
  
 **程序员提供的的信息**  
  
 因为程序未从操作系统以完成收到足够的内存，则会发生此错误[_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md)或`_beginthreadex`调用或线程本地存储尚未初始化由`_beginthread`或`_beginthreadex`。  
  
 新线程启动时，库必须为该线程创建一个内部数据库。 如果数据库无法通过使用操作系统提供的内存进行扩展，则该线程不会开始并且此调用进程会停止。 当此进程创建了过多线程或线程本地存储用完时，就会发生这种情况。  
  
 我们建议调用 C 运行库 (CRT) 的可执行文件，应使用`_beginthreadex`线程创建而不是 Windows API `CreateThread`。 `_beginthreadex` 将在线程本地存储中初始化很多 CRT 函数使用的内部静态存储。 如果使用 `CreateThread` 创建线程，则在调用需要初始化的内部静态存储的 CRT 函数时，CRT 可能会使用 R6016 终止此进程。
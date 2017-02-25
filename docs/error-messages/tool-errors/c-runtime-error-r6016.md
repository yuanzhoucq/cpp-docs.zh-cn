---
title: "C 运行时错误 R6016 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6016"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6016"
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# C 运行时错误 R6016
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

线程数据所需的空间不足  
  
> [!NOTE]
>  如果遇到此错误消息，则会关闭指定程序，因为它存在内部内存问题。  导致此错误的可能原因有很多，但通常是因为程序中存在缺陷或它使用的 Visual C\+\+ 库损坏。  
>   
>  可以尝试以下步骤来修复此错误：  
>   
>  -   使用**“控制面板”**中的**“程序和功能”**页来修复或重新安装该程序。  
> -   使用**“控制面板”**中的**“程序和功能”**页来修复或重新安装 Microsoft Visual C\+\+ Redistributable 的所有副本。  
> -   在**“控制面板”**的**“Windows Update”**中查看更新软件。  
> -   查看该程序的已更新版本。  
  
 发生此错误的原因在于，该程序未从操作系统中收到获得的内存来完成 [\_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) 或 `_beginthreadex` 调用，或者 `_beginthread` 或 `_beginthreadex` 尚未初始化线程本地存储。  
  
 新线程启动时，库必须为该线程创建一个内部数据库。  如果数据库无法通过使用操作系统提供的内存进行扩展，则该线程不会开始并且此调用进程会停止。  当此进程创建了过多线程或线程本地存储用完时，就会发生这种情况。  
  
 建议调用 C 运行时库 \(CRT\) 的可执行文件应该将 `_beginthreadex` 用于创建线程而不是 Windows API `CreateThread`。  `_beginthreadex` 将在线程本地存储中初始化很多 CRT 函数使用的内部静态存储。  如果使用 `CreateThread` 创建线程，则在调用需要初始化的内部静态存储的 CRT 函数时，CRT 可能会使用 R6016 终止此进程。
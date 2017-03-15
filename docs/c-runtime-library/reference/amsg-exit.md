---
title: "_amsg_exit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_amsg_exit"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_amsg_exit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_amsg_exit"
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# _amsg_exit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

发出指定的错误消息时发生运行时然后退出代码 255 的应用程序。  
  
## 语法  
  
```cpp  
void _amsg_exit (  
   int rterrnum  
   )  
  
```  
  
#### 参数  
 `rterrnum`  
 一个系统中定义的运行时错误消息的 ID。  
  
## 备注  
 此函数发出运行时错误消息写入控制台应用程序的 **stderr** 显示一个 MessageBox 的消息或在 Windows 应用程序中。  在调试模式下，可以选择在退出之前调用调试器。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|\_amsg\_exit|internal.h|
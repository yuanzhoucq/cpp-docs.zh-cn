---
title: "/HEAP | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/heap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "堆分配, 设置堆大小"
  - "HEAP editbin 选项"
  - "-HEAP editbin 选项"
  - "/HEAP editbin 选项"
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /HEAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置堆的大小，以字节为单位。  此选项仅适用于可执行文件。  
  
```  
  
/HEAP:  
reserve[,commit]  
  
```  
  
## 备注  
 `reserve` 参数指定虚拟内存中总的初始堆分配。  默认堆大小为 1 MB。  [EDITBIN 参考](../../build/reference/editbin-reference.md)链接器将指定值向上舍入为最接近的多个 4 字节。  
  
 可选 `commit` 参数取决于操作系统的解释。  在 Windows 操作系统，它指定最初分配的物理内存量和分发时的时间附加内存需要展开堆。  提交的虚拟内存导致空间被保留在页面文件中。  当应用需要更多空间堆，但会增加内存要求和潜在应用开始持续时间时，更高的 `commit` 值通常允许系统分配内存更少。  `commit` 的值必须小于或等于 `reserve` 的值。  
  
 指定 `reserve` 和 `commit` 值使用十进制或 C 语言十六进制或八进制表示形式。  例如，值 1 MB 可指定为十进制 1048576，或作为 十六进制数0x100000 ，或者用作八进制数04000000 。  
  
## 请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)
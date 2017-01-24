---
title: "/BIND | Microsoft Docs"
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
  - "/bind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/BIND editbin 选项"
  - "BIND editbin 选项"
  - "-BIND editbin 选项"
  - "入口点"
  - "入口点, 地址"
  - "导入地址表"
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /BIND
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/BIND[:PATH=path]  
```  
  
## 备注  
 此选项在导入地址表中为可执行文件或 DLL 设置入口点地址。  使用此选项可减少程序加载时间。  
  
 在 EDITBIN 命令行的 *files* 参数中指定程序的可执行文件和 DLL。  \/BIND 的可选 *path* 参数指定由指定文件使用的 DLL 的位置。  用分号 \(**;**\) 分隔多个目录。  如果没有指定 *path* 参数，则 EDITBIN 将搜索 PATH 环境变量中指定的目录。  如果指定了 *path* 参数，则 EDITBIN 将忽略 PATH 变量。  
  
 默认情况下，程序加载程序在加载程序时设置入口点地址。  此进程所需的时间因程序中引用的 DLL 数和入口点数而异。  如果已经用 \/BIND 修改了程序，并且可执行文件的基址及其 DLL 与已加载的 DLL 不冲突，则操作系统不需要设置这些地址。  如果文件的基址设置得不正确，操作系统将重新定位程序的 DLL 并重新计算入口点地址，而这会增加程序的加载时间。  
  
## 请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)
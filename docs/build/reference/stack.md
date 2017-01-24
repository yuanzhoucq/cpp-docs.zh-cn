---
title: "/STACK | Microsoft Docs"
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
  - "/stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/STACK editbin 选项"
  - "STACK editbin 选项"
  - "-STACK editbin 选项"
  - "堆栈, 设置大小"
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /STACK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/STACK:reserve[,commit]  
```  
  
## 备注  
 此选项设置堆栈的大小（以字节计），并带使用十进制或 C 语言表示法的参数。  \/STACK 选项仅适用于可执行文件。  
  
 *reserve* 参数指定虚拟内存中总的堆栈分配。  EDITBIN 将指定值四舍五入到最接近的 4 个字节。  
  
 可选 `commit` 参数取决于操作系统的解释。  在 Windows NT、Windows 95 和 Windows 98 中，`commit` 指定一次分配的物理内存量。  提交的虚拟内存导致空间被保留在页面文件中。  更高的 `commit` 值在应用程序需要更多堆栈空间时可节省时间，但会增加内存需求并可能延长启动时间。  
  
## 请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)
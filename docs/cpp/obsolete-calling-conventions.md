---
title: "已过时调用约定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__fortran"
  - "__pascal"
  - "__syscall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__fortran 关键字 [C++]"
  - "__pascal 关键字 [C++]"
  - "__syscall 关键字 [C++]"
  - "调用约定, 已过时"
  - "WINAPI"
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 已过时调用约定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 **\_\_pascal**、**\_\_fortran** 和 **\_\_syscall** 调用约定不再受支持。  通过使用支持的调用约定之一和适当的链接器选项，可以模拟其功能。  
  
 WINDOWS.H 现在支持 **WINAPI** 宏，该宏将转换为目标的适当调用约定。  在之前使用 **PASCAL** 或 **\_\_far \_\_pascal** 的位置使用 **WINAPI**。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [参数传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)
---
title: "浮点协处理器和调用约定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "浮点协处理器"
  - "浮点数字"
  - "浮点数字, 协处理器"
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 浮点协处理器和调用约定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果在为浮点协处理器编写程序集例程，必须保留浮点控制字和清理协处理器堆栈，除非您在返回 **float** 或 **double** 值（您的函数应通过 ST\(0\) 返回）。  
  
## 请参阅  
 [调用约定](../cpp/calling-conventions.md)
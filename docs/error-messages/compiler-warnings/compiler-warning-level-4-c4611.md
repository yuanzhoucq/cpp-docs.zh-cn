---
title: "编译器警告（等级 4）C4611 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4611"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4611"
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4611
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”和 C\+\+ 对象析构之间的交互是不可移植的  
  
 在一些平台上，包含 **catch** 的函数在超出范围时可能不支持析构的 C\+\+ 对象语义。  
  
 为了避免发生意外行为，请不要在有构造函数和析构函数的函数中使用 **catch**。  
  
 只发出一次该警告，请参见 [pragma warning](../../preprocessor/warning.md)。
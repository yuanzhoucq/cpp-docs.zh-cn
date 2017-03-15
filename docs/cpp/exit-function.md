---
title: "exit 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Exit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exit 函数"
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# exit 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

标准包含文件 STDLIB.H 中声明的 **exit** 函数将终止 C\+\+ 程序。  
  
 作为 **exit** 的参数提供的值将作为程序的返回代码或退出代码返回到操作系统。  按照约定，返回代码为零表示该程序已成功完成。  
  
> [!NOTE]
>  可以使用在 STDLIB.H 中定义的常量 `EXIT_FAILURE` 和 `EXIT_SUCCESS` 来指示程序是成功还是失败。  
  
 从 **main** 函数发出 `return` 语句等效于调用返回值作为其参数的 **exit** 函数。  
  
 有关详细信息，请参阅《运行时库参考》中的 [exit](../c-runtime-library/reference/exit-exit-exit.md)。  
  
## 请参阅  
 [程序终止](../cpp/program-termination.md)
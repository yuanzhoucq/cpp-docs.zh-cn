---
title: "C 运行时错误 R6033 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6033"
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# C 运行时错误 R6033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

尝试在本机代码初始化过程中从此程序集使用 MSIL 代码。这指示您的应用程序中有 bug。导致此错误最可能的原因是从本机构造函数或从 DllMain 调用 MSIL 编译的 \(\/clr\) 函数。  
  
 此诊断指示在存在加载程序锁的过程中执行了 MSIL 指令。  有关详细信息，请参阅[混合程序集的初始化](../../dotnet/initialization-of-mixed-assemblies.md)。
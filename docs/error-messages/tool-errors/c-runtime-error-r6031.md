---
title: "C 运行时错误 R6031 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6031"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6031"
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# C 运行时错误 R6031
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

尝试多次初始化 CRT。这指示您的应用程序中有 bug。  
  
 此诊断指示在存在加载程序锁的过程中执行了 MSIL 指令。  有关详细信息，请参阅[混合程序集的初始化](../../dotnet/initialization-of-mixed-assemblies.md)。
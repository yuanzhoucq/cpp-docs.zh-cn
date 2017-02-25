---
title: "开发您自己的 Helper 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Helper 函数"
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 开发您自己的 Helper 函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您也许想提供自己的例程版本以进行基于 DLL 名称或导入名称的特定处理。  有两种方法可以执行此操作：编写您自己的代码（可能是在所提供的代码的基础上编写），或者仅用前面详细介绍过的通知挂钩与所提供的版本挂钩。  
  
 编写您自己的代码  
 这很简单，因为实际上您可以用所提供的代码做为新代码的指南。  当然，它必须遵守调用约定，而且如果它返回到链接器生成的 thunk，就必须返回正确的函数指针。  一旦您自己编写代码，就可以做许多想做的操作以满足调用或退出调用。  
  
 使用启动处理通知挂钩  
 最容易的方法可能就是只提供一个指向用户提供的通知挂钩函数的新指针，该函数接收的值与通知 dliStartProcessing 上的默认 Helper 接收的值相同。  在这一点上，挂钩函数基本上可以成为一个新的 Helper 函数，因为，到默认 Helper 的返回如果成功了，那么所有要在默认 Helper 函数中执行的进一步处理将跳过。  
  
## 请参阅  
 [链接器的延迟加载 DLL 支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)
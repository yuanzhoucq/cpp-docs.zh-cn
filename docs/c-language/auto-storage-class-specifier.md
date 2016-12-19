---
title: "auto 存储类说明符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto 存储类说明符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**auto** 存储类说明符可声明自动变量，即具有本地生存期的变量。  **auto** 变量仅在声明它的块中可见。  **auto** 变量的声明可包含初始值设定项，如[初始化](../c-language/initialization.md)中所述。  由于具有 **auto** 存储类的变量不会自动初始化，因此您应该在声明这些变量时对其进行显式初始化，或在块的语句中为其分配初始值。  未初始化的 **auto** 变量的值是不确定的。（如果给定了初始值设定项，则每次 **auto** 或 **register** 存储类的本地变量进入此范围时都会被初始化。）  
  
 内部 **static** 变量（具有本地或块范围的静态变量）可以使用任何外部或 **static** 项的地址进行初始化，但不能使用另一个 **auto** 项的地址进行初始化，因为 **auto** 项的地址不是常量。  
  
## 请参阅  
 [auto 关键字](../cpp/auto-keyword.md)
---
title: "main 函数限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Main"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "主函数, 使用限制"
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# main 函数限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

多个限制适用于不会应用于任何其他 C\+\+ 函数的 **main** 函数。  **main** 函数：  
  
-   无法重载（请参阅[重载](../misc/overloading-cpp.md)）。  
  
-   不能声明为 **inline**。  
  
-   不能声明为 **static**。  
  
-   不能提取其地址。  
  
-   无法被调用。  
  
## 请参阅  
 [main：程序启动](../cpp/main-program-startup.md)
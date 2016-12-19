---
title: "Varargs | Microsoft Docs"
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
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Varargs
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果参数是通过 vararg（例如省略号参数）传递的，则基本上会应用正常的参数传递过程，包括溢出第五个及后续参数。  此外，被调用方的责任是转储采用其地址的参数。  仅处理浮点值时，如果被调用方要使用整数寄存器中的值，整数寄存器和浮点寄存器才会同时包含浮点值。  
  
## 请参阅  
 [调用约定](../build/calling-convention.md)
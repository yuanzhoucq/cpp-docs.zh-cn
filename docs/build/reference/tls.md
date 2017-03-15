---
title: "/TLS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/TLS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/TLS dumpbin 选项"
  - "-TLS dumpbin 选项"
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# /TLS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从可执行程序显示 IMAGE\_TLS\_DIRECTORY 结构。  
  
## 备注  
 \/TLS 显示 TLS 结构的字段，以及 TLS 回调函数的地址。  
  
 如果程序不使用线程本地存储区，它的映像将不包含 TLS 结构。有关更多信息，请参见[线程](../../cpp/thread.md)。  
  
 IMAGE\_TLS\_DIRECTORY 在 winnt.h 中定义。  
  
## 请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)
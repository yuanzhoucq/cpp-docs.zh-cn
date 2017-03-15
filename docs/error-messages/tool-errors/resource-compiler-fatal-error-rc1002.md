---
title: "资源编译器错误 RC1002 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC1002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1002"
ms.assetid: b43dfece-0dc3-4d0b-9d8f-509699b9ae80
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 资源编译器错误 RC1002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

堆空间不足  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  增大 Windows 交换文件空间。  有关增大交换文件空间的更多信息，请参见 Windows 帮助中的虚拟内存。  
  
2.  将当前文件拆分为几个较小的文件然后分别编译。  
  
3.  移除系统上正在运行的其他程序或驱动程序。
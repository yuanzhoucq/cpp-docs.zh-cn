---
title: "预编译头一致性规则 | Microsoft Docs"
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
  - "预编译的头文件, 一致性规则"
ms.assetid: 844b1a14-5b0b-4276-a1f5-cc62f13f6dda
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 预编译头一致性规则
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本节论述有助于更有效地使用预编译头的准则：  
  
-   [按文件使用预编译头的一致性规则](../../build/reference/consistency-rules-for-per-file-use-of-precompiled-headers.md)  
  
-   [\/Yc 和 \/Yu 的一致性规则](../../build/reference/consistency-rules-for-yc-and-yu.md)  
  
 由于 PCH 文件包含关于计算机环境的信息以及关于程序的内存地址的信息，所以仅应使用创建它的计算机上的 PCH 文件。  
  
## 请参阅  
 [创建预编译的头文件](../../build/reference/creating-precompiled-header-files.md)
---
title: "BSCMAKE 错误 BK1509 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK1509"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1509"
ms.assetid: 53df7037-1913-4b63-b425-c0bf44081792
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# BSCMAKE 错误 BK1509
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

堆空间不足  
  
 BSCMAKE 内存不足（包括虚拟内存）。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  释放一些磁盘空间。  
  
2.  增加交换文件大小。  
  
3.  增加 Windows 交换文件大小。  
  
4.  使用 \/Ei 或 \/Es 消除一些输入文件或使用 \/Em 消除宏体以减小 BSCMAKE 所需内存。
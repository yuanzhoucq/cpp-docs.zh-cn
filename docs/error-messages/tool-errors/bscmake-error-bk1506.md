---
title: "BSCMAKE 错误 BK1506 | Microsoft Docs"
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
  - "BK1506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1506"
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# BSCMAKE 错误 BK1506
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法打开文件“文件名”\[: 原因\]  
  
 BSCMAKE 无法打开文件。  
  
### 通过检查以下可能的原因进行修复  
  
1.  文件被另一进程锁定。  如果给出的 `reason` 是“权限被拒绝”，则浏览器可能正在使用该文件。  关闭“浏览”窗口并重试生成。  
  
2.  磁盘已满。  
  
3.  硬件错误。  
  
4.  指定的输出文件与现有子目录同名。
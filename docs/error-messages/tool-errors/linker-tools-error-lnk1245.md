---
title: "链接器工具错误 LNK1245 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1245"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1245"
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 链接器工具错误 LNK1245
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定的子系统“subsystem”无效；\/SUBSYSTEM 必须是 WINDOWS、WINDOWSCE 或 CONSOLE  
  
 使用了 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 编译对象并且存在下列情况之一：  
  
-   定义了自定义入口点 \([\/ENTRY](../../build/reference/entry-entry-point-symbol.md)\)，因此链接器未能推导出子系统。  
  
-   值传递给了对 \/clr 对象无效的 [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) 链接器选项。  
  
 对于这两种情况，解决方法是为 \/SUBSYSTEM 链接器选项指定一个有效值。
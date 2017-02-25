---
title: "编译器警告（等级 3）C4278 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4278"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4278"
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 3）C4278
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 类型库“tlb”中的标识符已经是宏；使用“rename”限定符  
  
 在使用 [\#import](../../preprocessor/hash-import-directive-cpp.md) 时，您正导入的类型库中的标识符尝试声明标识符 ***identifier***。  然而这已是一个有效符号。  
  
 使用 `#import` **rename** 特性为类型库中的符号分配别名。
---
title: "使用导入库和导出文件 | Microsoft Docs"
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
  - "导出文件"
  - "导入库"
  - "导入库, 创建"
  - "LIB [C++], /DEF 选项"
  - "LIB [C++], 导入库和导出文件"
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用导入库和导出文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可使用带 \/DEF 选项的 LIB 来创建导入库和导出文件。  LINK 使用导出文件生成包含导出的程序（通常是动态链接库 \(DLL\)），并使用导入库解析其他程序中对这些导出的引用。  
  
 请注意，如果您在预备步骤中创建了导入库，则在创建 .dll 之前，生成 .dll 时必须传递生成导入库时所传递的同一组对象文件。  
  
 大多数情况下，不需要使用 LIB 创建导入库。  在链接包含导出的程序（可执行文件或 DLL）时，LINK 自动创建描述导出的导入库。  以后，在链接引用那些导出的程序时指定导入库。  
  
 但是，如果 DLL 导出到的程序同时也是它从中导入的程序，则无论是直接还是间接导入，都必须使用 LIB 创建其中某个导入库。  LIB 在创建导入库时还创建导出文件。  在链接其中某个 DLL 时必须使用导出文件。  
  
## 请参阅  
 [LIB 引用](../../build/reference/lib-reference.md)
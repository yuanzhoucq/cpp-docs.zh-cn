---
title: "LIB 输出文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Lib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "输出文件, LIB"
ms.assetid: e73d2f9b-a42d-402b-b7e3-3a94bebb317e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# LIB 输出文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LIB 所产生的输出文件取决于它的使用模式，如下表所示。  
  
|Mode|Output|  
|----------|------------|  
|默认模式（生成或修改库）|COFF 库 \(.lib\)|  
|使用 \/EXTRACT 提取成员|对象 \(.obj\) 文件|  
|使用 \/DEF 生成导出文件和导入库|导入库 \(.lib\) 和导出 \(.exp\) 文件|  
  
## 请参阅  
 [LIB 概述](../../build/reference/overview-of-lib.md)
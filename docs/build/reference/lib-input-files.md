---
title: "LIB 输入文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
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
  - "输入文件, LIB"
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LIB 输入文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LIB 所需的输入文件取决于它的使用模式，如下表所示。  
  
|Mode|输入|  
|----------|--------|  
|默认模式（生成或修改库）|COFF 对象 \(.obj\) 文件、COFF 库 \(.lib\)、32 位对象模型格式 \(OMF\) 对象 \(.obj\) 文件|  
|使用 \/EXTRACT 提取成员|COFF 库 \(.lib\)|  
|使用 \/DEF 生成导出文件和导入库|模块定义 \(.def\) 文件、COFF 对象 \(.obj\) 文件、COFF 库 \(.lib\)、32 位 OMF 对象 \(.obj\) 文件|  
  
> [!NOTE]
>  16 位版本 LIB 创建的 OMF 库不能用作 32 位版本的 LIB 的输入。  
  
## 请参阅  
 [LIB 概述](../../build/reference/overview-of-lib.md)
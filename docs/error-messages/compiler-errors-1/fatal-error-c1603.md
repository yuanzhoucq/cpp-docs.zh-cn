---
title: "错误 C1603 | Microsoft Docs"
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
  - "C1603"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1603"
ms.assetid: e5a06925-f916-4637-8240-6d2d280e6124
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1603
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

内联程序集分支目标超出范围“number”个字节  
  
 JCXZ 或 JECXZ 指令与它的指定目标标签之间的计算距离大于 128 字节。  更新代码以使标签更接近指令。
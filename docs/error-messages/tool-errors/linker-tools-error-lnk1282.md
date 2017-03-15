---
title: "链接器工具错误 LNK1282 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1282"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1282"
ms.assetid: 99c13f52-eb80-46ce-a5b9-4537583e32a9
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 链接器工具错误 LNK1282
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法 \/REBASE 文件；已对它进行签名  
  
 您尝试使用 [editbin](../../build/reference/editbin-reference.md) 的 \/REBASE 选项更改已签名程序集的基址。  为此，首先更改基址，然后再对程序集进行签名。
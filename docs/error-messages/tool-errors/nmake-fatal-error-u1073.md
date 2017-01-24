---
title: "NMAKE 错误 U1073 | Microsoft Docs"
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
  - "U1073"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1073"
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 错误 U1073
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不知道如何生成“targetname”  
  
 指定的目标不存在，而且没有要执行的命令或要应用的推理规则。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  检查目标名称的拼写。  
  
2.  如果 *targetname* 是伪目标，则将它指定为另一个描述块中的目标。  
  
3.  如果 *targetname* 是宏调用，则确保它不扩展到空字符串。
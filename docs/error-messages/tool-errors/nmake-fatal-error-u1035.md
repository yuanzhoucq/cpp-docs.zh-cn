---
title: "NMAKE 错误 U1035 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1035"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1035"
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# NMAKE 错误 U1035
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

语法错误 : 应输入“:”或“\=”分隔符  
  
 应输入冒号 \(**:**\) 或等号 \(**\=**\)。  
  
### 通过检查以下可能的原因进行修复  
  
1.  冒号未跟在目标的后面。  
  
2.  无空格的冒号（如 a:）跟在了单字母目标的后面。  NMAKE 将其解释为驱动器规格。  
  
3.  冒号未跟在推理规则的后面。  
  
4.  宏定义的后面没有等号。  
  
5.  字符跟在了用于将命令继续到新行的反斜杠 \(**\\**\) 的后面。  
  
6.  出现未遵循任何 NMAKE 语法规则的字符串。  
  
7.  字处理器已将生成文件格式化。
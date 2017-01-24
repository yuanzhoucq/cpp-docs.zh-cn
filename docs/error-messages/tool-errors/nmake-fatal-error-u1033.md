---
title: "NMAKE 错误 U1033 | Microsoft Docs"
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
  - "U1033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1033"
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 错误 U1033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

语法错误 : 意外的“string”  
  
 该字符串不是生成文件的有效语法的一部分。  
  
### 通过检查以下可能的原因进行修复  
  
1.  如果内联文件的右尖括号组 \(**\<\<**\) 不在行首，则出现下列错误：  
  
    ```  
    syntax error : 'EOF' unexpected  
    ```  
  
2.  如果生成文件中的宏定义包含前面没有名称的等号 \(**\=**\)，或正被定义的名称是扩展到 nothing 的宏，则出现下列错误：  
  
    ```  
    syntax error : '=' unexpected  
    ```  
  
3.  如果 TOOLS.INI 中注释行中的分号 \(**;**\) 不在该行的开始处，则出现下列错误：  
  
    ```  
    syntax error : ';' unexpected  
    ```  
  
4.  如果字处理器已将生成文件格式化，则会出现下列错误：  
  
    ```  
    syntax error : ':' unexpected  
    ```
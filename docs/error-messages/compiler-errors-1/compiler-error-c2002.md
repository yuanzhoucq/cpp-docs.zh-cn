---
title: "编译器错误 C2002 | Microsoft Docs"
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
  - "C2002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2002"
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无效的宽字符常数  
  
 多字节字符常数是无效的。  
  
### 通过检查以下可能的原因进行修复  
  
1.  宽字符常数包含的字节比需要的多。  
  
2.  未包括标准头文件 STDDEF.h。  
  
3.  宽字符不能与一般字符串连接。  
  
4.  宽字符常数之前必须是字符“L”：  
  
    ```  
    L'mbconst'  
    ```  
  
5.  对于 Microsoft C\+\+，预处理器指令的文本参数必须是 ASCII。  例如，指令 `#pragma message(L"string")` 是无效的。
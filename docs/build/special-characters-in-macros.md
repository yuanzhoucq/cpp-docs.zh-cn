---
title: "宏内的特殊字符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "特殊字符, 在 NMAKE 宏中"
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 宏内的特殊字符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

位于定义之后的数字符号 \(\#\) 指定注释。  若要在宏内指定数字符号，请使用插入符号 \(^\)，如在 ^\# 中。  
  
 美元符号 \($\) 指定宏调用。  若要指定文本 $，请使用 $$。  
  
 若要将定义扩展到新行，请以反斜杠 \(\\\) 结束行。  调用宏后，用空格替换反斜杠和换行符。  若要在行尾指定文本反斜杠，请在它的前面添上插入符号 \(^\)，或后面跟注释说明符 \(\#\)。  
  
 若要指定文本换行符，用插入符号 \(^\) 结束行，如下所示：  
  
```  
CMDS = cls^  
dir  
```  
  
## 请参阅  
 [定义 NMAKE 宏](../build/defining-an-nmake-macro.md)
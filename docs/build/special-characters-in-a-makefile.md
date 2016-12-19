---
title: "生成文件中的特殊字符 | Microsoft Docs"
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
  - "宏, 特殊字符"
  - "生成文件, 特殊字符"
  - "NMAKE 程序, 特殊字符"
  - "特殊字符, 在 NMAKE 宏中"
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 生成文件中的特殊字符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要将 NMAKE 特殊字符用作文字字符，请在它前面添一插入符号 \(^\)。  NMAKE 忽略其他字符前面的插入符号。  特殊字符为：  
  
 `:  ;  #  (  )  $  ^  \  {  }  !  @  —`  
  
 引号引起来的字符串内的插入符号 \(^\) 被视为 ^ 字符。  在字符串或宏中，位于行尾的插入符号插入换行符。  
  
 在宏中，后面跟有换行符的反斜杠 \(\\\) 由空格替换。  
  
 在命令中，百分号 \(%\) 是文件说明符。  若要在命令中按原义表示 %，请指定两个百分号 \(%%\) 取代一个百分号。  在其他情况中，NMAKE 按原义解释一个 %，但它总将两个 %% 解释为一个 %。  因此，若要表示 %%，请指定三个百分号 %%%，或四个百分号 %%%%。  
  
 若要将美元符号 \($\) 用作命令中的文字字符，请指定两个美元符号 \($$\)。  此方法还可用于 ^$ 有效的其他情况。  
  
## 请参阅  
 [生成文件的内容](../build/contents-of-a-makefile.md)
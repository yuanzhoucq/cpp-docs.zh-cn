---
title: "资源编译器错误 RC2001 | Microsoft Docs"
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
  - "RC2001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2001"
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 资源编译器错误 RC2001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

常数中有换行符  
  
 字符串常数在第二行继续，既没有反斜杠 \(**\\**\) 也没有右双引号和左双引号 \(**"**\)。  
  
 若要断开源文件中位于两行上的字符串常数，执行下列任一操作：  
  
-   以行继续符（反斜杠）结束第一行。  
  
-   用一个双引号结束第一行上的字符串并在下一行用另一个双引号开始该字符串。  
  
 用 \\n（将换行符嵌入字符串常数的换码序列）结束第一行是不够的。
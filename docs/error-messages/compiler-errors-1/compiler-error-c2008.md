---
title: "编译器错误 C2008 | Microsoft Docs"
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
  - "C2008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2008"
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“character”: 宏定义中的意外  
  
 该字符紧跟在宏名之后。  若要解决该错误，宏名之后必须有一个空格。  
  
 下面的示例生成 C2008：  
  
```  
// C2008.cpp  
#define TEST1"mytest1"    // C2008  
```  
  
 可能的解决方案：  
  
```  
// C2008b.cpp  
// compile with: /c  
#define TEST2 "mytest2"  
```
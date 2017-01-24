---
title: "字符化运算符 (#@) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#@"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#@ 预处理器运算符"
  - "字符化运算符"
  - "预处理器, 运算符"
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 字符化运算符 (#@)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 charizing 运算符只能与宏的参数一起使用。  如果宏的定义中的形参前有 **\#@**，则会在扩展宏时用单引号括起实参并将其视为一个字符。  例如：  
  
```  
#define makechar(x)  #@x  
```  
  
 导致以下语句  
  
```  
a = makechar(b);  
```  
  
 扩展为  
  
```  
a = 'b';  
```  
  
 单引号字符不能与 charizing 运算符一起使用。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [预处理器运算符](../preprocessor/preprocessor-operators.md)
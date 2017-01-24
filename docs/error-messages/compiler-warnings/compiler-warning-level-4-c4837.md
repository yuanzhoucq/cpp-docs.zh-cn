---
title: "编译器警告（等级 4）C4837 | Microsoft Docs"
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
  - "C4837"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4837"
ms.assetid: 9a3c7b6b-ffe4-443d-96af-43deb80d85b4
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4837
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检测到三元祖:“??%c”已替换为“%c”  
  
 检测到的三字符组由指示的字符所替换。  
  
 编译器会在完成任何其他处理之前转换三字符组。  使用字符转义序列 `\?` 可防止对类似于三字符组的字符序列进行错误解释。  有关三字符组的更多信息，请参见[三字符组](../../c-language/trigraphs.md)。  有关转义序列的更多信息，请参见[转义序列](../../c-language/escape-sequences.md)。  
  
 默认情况下，C4837 处于关闭状态。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
### 更正此错误  
  
1.  使用字符转义序列 `\?` 替换源代码中的一个“?”字符。  
  
## 请参阅  
 [三字符组](../../c-language/trigraphs.md)   
 [转义序列](../../c-language/escape-sequences.md)   
 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)
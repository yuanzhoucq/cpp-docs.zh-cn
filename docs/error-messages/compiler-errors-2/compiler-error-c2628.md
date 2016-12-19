---
title: "编译器错误 C2628 | Microsoft Docs"
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
  - "C2628"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2628"
ms.assetid: 19a25e77-d5be-4107-88d5-0745b6281f98
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2628
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type1”后面接“type2”是非法的\(是否忘记了“;”？\)  
  
 可能缺少分号。  
  
 下面的示例生成 C2628：  
  
```  
// C2628.cpp  
class CMyClass {}  
int main(){}   // C2628 error  
```  
  
 可能的解决方案：  
  
```  
// C2628b.cpp  
class CMyClass {};  
int main(){}  
```
---
title: "编译器错误 C3666 | Microsoft Docs"
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
  - "C3666"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3666"
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3666
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“constructor”: 重写说明符“keyword”不允许在构造函数上使用  
  
 禁止在构造函数上使用重写说明符。  有关详细信息，请参阅[重写说明符](../../windows/override-specifiers-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C3666。  
  
```  
// C3666.cpp  
// compile with: /clr /c  
ref struct R {  
   R() new {}   // C3666  
   R(int i) {}   // OK  
};  
```
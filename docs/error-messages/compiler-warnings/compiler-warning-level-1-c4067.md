---
title: "编译器警告（等级 1）C4067 | Microsoft Docs"
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
  - "C4067"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4067"
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4067
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

预处理器指令后有意外标记 \- 应输入换行符  
  
 编译器发现预处理器指令之后有多余字符，并忽略它们。  此警告只会在 ANSI 兼容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 情况下出现。  
  
```  
// C4067a.cpp  
// compile with: /DX /Za /W1  
#pragma warning(default:4067)  
#if defined(X)  
#else  
#endif v   // C4067  
int main()  
{  
}  
```  
  
### 若要解决此警告，请尝试以下操作：  
  
1.  用 **\/Ze** 编译  
  
2.  使用注释分隔符：  
  
```  
// C4067b.cpp  
// compile with: /DX /Za /W1  
#if defined(X)  
#else  
#endif  
int main()  
{  
}  
```
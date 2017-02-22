---
title: "编译器警告（等级 1）C4216 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4216"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4216"
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4216
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展 : 长浮点  
  
 默认 Microsoft 扩展 \(\/Ze\) 将 **float long** 视为 **double**。  ANSI 兼容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 则不是这样。  请使用 **double** 以维护兼容性。  下面的示例生成 C4216：  
  
```  
// C4216.cpp  
// compile with: /W1  
float long a;   // C4216  
  
// use the line below to resolve the warning  
// double a;  
  
int main() {  
}  
```
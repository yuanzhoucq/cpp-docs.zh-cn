---
title: "编译器警告（等级 1）C4129 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4129"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4129"
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4129
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“character”: 不可识别的字符转义序列  
  
 字符常数或字符串常数中反斜杠 \(\\\) 之后的 `character` 未被识别为有效转义序列。  忽略该反斜杠，并且不将其输出。  输出反斜杠之后的字符。  
  
 若要输出一个反斜杠，请指定一个双反斜杠 \(\\\\\)。  
  
 2.13.2 节中的 C\+\+ 标准讨论了转义序列。  
  
 下面的示例生成 C4129：  
  
```  
// C4129.cpp  
// compile with: /W1  
int main() {  
   char array1[] = "\/709";   // C4129  
   char array2[] = "\n709";   // OK  
}  
```
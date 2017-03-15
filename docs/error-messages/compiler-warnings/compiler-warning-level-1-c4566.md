---
title: "编译器警告（等级 1）C4566 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4566"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4566"
ms.assetid: 65f40730-e86f-447c-b37b-16caadcfe311
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4566
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

由通用字符名称“char”表示的字符不能在当前代码页 \(page\) 中表示  
  
 并非每个 Unicode 字符都可在当前 ANSI 代码页中表示。  
  
 窄字符串（单字节字符）转换为多字节字符，而宽字符串（双字节字符）不转换。  
  
 下面的示例生成 C4566：  
  
```  
// C4566.cpp  
// compile with: /W1  
int main() {  
   char c1 = '\u03a0';   // C4566  
   char c2 = '\u0642';   // C4566  
  
   wchar_t c3 = L'\u03a0';   // OK  
   wchar_t c4 = L'\u0642';   // OK  
}  
```
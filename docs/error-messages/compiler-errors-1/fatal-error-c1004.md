---
title: "错误 C1004 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1004"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1004"
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 错误 C1004
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

遇到意外的文件结束  
  
 编译器到达了源文件尾但未解析构造。  代码可能缺少以下元素之一：  
  
-   右大括号  
  
-   右括号  
  
-   结束的注释标记 \(\*\/\)  
  
-   分号  
  
 若要解决此错误，请检查以下内容：  
  
-   默认磁盘驱动器没有足够的空间用于临时文件，需要大约两倍于源文件的空间。  
  
-   计算结果为假的 `#if` 指令缺少结束的 `#endif` 指令。  
  
-   源文件不是以回车和换行结束。  
  
 下面的示例生成 C1004：  
  
```  
// C1004.cpp  
#if TEST  
int main() {}  
// C1004  
```  
  
 可能的解决方案：  
  
```  
// C1004b.cpp  
#if TEST  
#endif  
  
int main() {}  
```
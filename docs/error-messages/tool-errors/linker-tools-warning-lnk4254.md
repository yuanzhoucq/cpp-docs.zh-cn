---
title: "链接器工具警告 LNK4254 | Microsoft Docs"
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
  - "LNK4254"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4254"
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4254
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

节“section1”\(offset\) 合并到具有不同特性的“section2”\(offset\)  
  
 某一节的内容合并到另一节中，但是两个节的特性不同。  程序可能生成意外的结果。  例如，希望使其为只读的数据现在可能在可写节中。  
  
 若要解决 LNK4254，请修改或移除合并请求。  
  
 在面向具有 Visual C\+\+ 的 x86 计算机和 Windows CE 目标（ARM、MIPS、SH4 和 Thumb）时，.CRT 节是只读的。  如果您的代码依赖于以前的行为（.CRT 节具有可读\/可写性），则您可能会看到意外的行为。  
  
 有关详细信息，请参阅  
  
-   [\/MERGE（合并节）](../../build/reference/merge-combine-sections.md)  
  
-   [注释](../../preprocessor/comment-c-cpp.md)  
  
## 示例  
 下面的示例生成 LNK4254。  
  
```  
// LNK4254.cpp  
// compile with: /W1 /link /WX  
// LNK4254 expected  
#pragma comment(linker, "/merge:.data=.text")  
int main() {}  
```
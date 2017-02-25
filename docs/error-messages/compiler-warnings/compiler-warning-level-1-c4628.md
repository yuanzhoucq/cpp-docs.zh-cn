---
title: "编译器警告（等级 1）C4628 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4628"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4628"
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4628
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\-Ze 不支持二合字母。字符序列“digraph”未解释为“char”的替换标记  
  
 在 [\/Ze](../../build/reference/za-ze-disable-language-extensions.md) 下不支持二合字母。  此警告后将跟有某一错误。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的示例生成 C4628：  
  
```  
// C4628.cpp  
// compile with: /WX  
#pragma warning(default : 4628)  
int main()  
<%   // C4628 <% digraph for {  
}  
```